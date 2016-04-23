---
id: 12251
title: 'MetaDapper: Data Mapping and Conversion Made Easy With the Right Tools'
date: 2016-01-05T16:50:01+00:00
author: Irina Papuc
layout: post
guid: http://giscollective.org/?p=12251
categories:
  - Data
---
Data conversion, translation, and mapping is by no means rocket science, but it is by all means tedious. Even a simple data conversion task (e.g., reading a CSV file into a list of class instances) can require a non-trivial amount of code. While all of these tasks share much in common, they are all “just different enough” to require their own data conversion methods.

In virtually every system that we build, we will at some point find ourselves needing to transform data from one form to another, whether for importing data from an existing data store, processing data from an incoming stream, translating from one format to another for internal processing, or transforming data to a desired output format.

And each time we do so, the task seems so frustratingly similar to what we’ve done so many times before, yet has just enough differences to require us to do the data mapping process all over again, largely from scratch.

Moreover, as the most popular formats and technologies for accessing them continue to evolve, and new ones are introduced and gain popularity, programmers are obliged to constantly learn new data conversion and mapping techniques, libraries, APIs, and frameworks.

Although you can leverage tools like [AutoMapper](http://automapper.org/) (to map data from one object to another) or [Resharper](http://www.jetbrains.com/resharper/)(to refactor existing code), no matter what you do, the code will be tedious to write and will always need to be maintained. And then you have to come up with a solution for cross domain translation handling – like converting internal codes and key values to values for another layer or system, null values to default values, type conversion, etc. Validation has similar issues that are addressed by technologies like [DataAnnotations](http://bradwilson.typepad.com/blog/2009/04/dataannotations-and-aspnet-mvc.html) and the jQuery Validation plugin and by reams of custom validation code. And the nuances with each of these technologies can be quite subtle.

As an [advanced data scientist](http://www.toptal.com/data-science), you tell yourself “There’s got to be a better way.” Well, in fact, there is. And that’s what this data mapping tutorial is about.

## Introducing the MetaDapper Data Mapping Tool

![](http://assets.toptal.io/uploads/blog/image/587/toptal-blog-image-1410466431238.jpg)

MetaDapper is a .NET library that strives to simplify and streamline the data conversion process to the greatest extent possible.

MetaDapper facilitates data conversion by:

  * Decoupling the repeatable boilerplate portions of the data
  
    conversions process from those aspects that are unique to each data
  
    transformation task.
  * Providing an easy-to-use, intuitive user interface for specifying mapping and translation rules of arbitrary complexity.

MetaDapper separates logical mapping (schema, data translation, and validation) from physical data mapping (conversion to and from various file formats and APIs). The logical mapping features a powerful set of functions and allows you to hook in your own methods to handle very specific needs. The physical mapping includes a rich set of supported formats that are being extended constantly. To configure a mapping, the MetaDapper Configurator is provided; a simple to use Windows executable for creating and editing mappings, and for executing them for testing or for one-off conversions.

Converting a list of class instances to XML or CSV files, populating SQL database records, generating SQL scripts for populating tables, creating spreadsheets, and much more, is all done using the same configuration file that can often be created in seconds.

To include MetaDapper in your [.NET program](http://www.toptal.com/dot-net/dotnet-core-going-wild-and-open-source-what-took-you-so-long), you simply need to:

  * Add a reference to the library
  * Instantiate the MetaDapper engine
  * Execute the mapping, specifying the source reader (and any parameters), the destination writer (and any parameters), and your configuration file.

On success, the writer will output the transformed data. On error, an exception will give back detailed error information so you can reject the data or tune the configuration.

Here’s a brief data mapping example:

    List<MyClass> result;
    try
    {
        // Instantiate the MetaDapper library.
        var log = new Log();
        var cultureInfo = new CultureInfo("en-US");
        var md = new MetaDapper.Engine.MetaDapper(log, cultureInfo);
    
        using (var inputStream = new StreamReader(@"C:\myfile.csv"))
        {
            md.MapData(
                new CsvReaderParameters
                {
                    Log = log, CultureInfo = cultureInfo,
                    InputStream = inputStream.BaseStream, InputEncoding = Encoding.ASCII,
                    FirstRecordIsHeader = false
                },
                new PublicPropertiesWriterParameters
                {
                    Log = log, CultureInfo = cultureInfo
                },
                @"C:\MyMetaDapperConfiguration.xml", false, out result);
        }
    }
    catch (Exception)
    {
        throw;
    }
    

## The MetaDapper “Configurator”

The MetaDapper Configurator provides a way to visually walk through the steps of defining your data structure and conversion/mapping rules. The Configurator enables you to create, edit, and execute configurations (i.e., for testing or one-off conversions).

MetaDapper’s Configurator strives to automate as much of the process as possible. For example, when specifying a field mapping, the source and destination fields are matched up automatically when possible using name matching. Also, when creating Record Definitions for data sources that contain metadata, the field definitions can be populated automatically by pointing at the data source.

Once created, a Record Definition maintains its link to the data source it was created from (if any) so it can be automatically updated if the data source schema subsequently changes. When configuring a Record Definition for a data source with little or no metadata available, if another similar data source is available that does contain metadata, that Record Definition can be copied (with its metadata) to serve as the basis for the new Record Definition and can then be edited to reflect any differences that may exist between the two data sources. And in cases where the schema and metadata is identical for multiple data sources, a single Record Definition can be used for them all.

## Simplifying the data conversion process

Let’s look in more detail at some of the challenges inherent in the data conversion process and the ways in which MetaDapper facilitates and simplifies them for the developer.

## Mapping source to destination data

When an internal or external structure is changed in the course of maintenance, any mapping code that relies on these structures may need to be adjusted as well. This is an area where maintenance work is often required, so whatever solution you use, the maintenance costs need to be evaluated. For example, if a TotalSale property is removed from a Sale class, any related mapping assignments need to be adjusted accordingly.

With MetaDapper, updating a mapping may take as little as a few seconds. For a class type, for example, simply click the “Import field definitions from class” button to refresh the fields to the newly compiled definition:

![](http://assets.toptal.io/uploads/blog/image/552/toptal-blog-image-1410442439671.png)

## Type conversion

Some type conversions, such as Date/Time and Number type conversions for example, are sensitive to the host environment’s international settings (unless explicitly specified in code). Deploying an application on a new server with different international settings can therefore break code that doesn’t take this into account. A date value of “1-2-2014”, for example, will be interpreted as Jan. 2, 2014 in a machine with U.S. settings, but as Feb. 1, 2014 on a machine with U.K. settings. MetaDapper supports all implicit .NET conversions and allows for complex reformatting of values as part of the translation as well. Moreover, separate (i.e., independent) international settings can be specified in MetaDapper readers, writers, and the mapping engine.

## Complex default values

Sometimes, specific business rules that require access to other systems, or require complex coding, to determine a default value are needed. MetaDapper allows any number of custom delegate methods to be registered with the engine and employed to provide default values, perform custom data conversion, and to provide custom field validation.

## Conditional validation rules

It is not uncommon for field values to be required conditionally (or even for their valid values to be dependent on the values of other fields). For example, it might be the case that Partner Name and Partner Social Security Code fields can be left blank, but if a Partner Name is provided, then the Partner Social Security Code (and possibly other fields) must be provided. This type of conditional validation is complex and is easy to get wrong in custom code. By contrast, MetaDapper allows this kind of data mapping relationship to be easily configured. Specifically, a list of fields in a Record Definition can be listed in a Conditional Mandatory Fields Group:

![](http://assets.toptal.io/uploads/blog/image/553/toptal-blog-image-1410442609100.png)

Then in a mapping, the group can be associated with any field which, if not null, would in turn require all fields in the group to be supplied. For example:

![](http://assets.toptal.io/uploads/blog/image/554/toptal-blog-image-1410442619397.png)

## Converting mapped values across domains

Source data may contain inconsistent values. For example, a salutation field may contain “Mr.”, “Mr”, “MR.”, “Mister” or “M” as well as all the female equivalents. Or a currency field may contain a value like “$” while your destination format requires “USD”. Product codes are another example of values that may need to be converted from one system to another. MetaDapper allows for the specification of reusable “synonym lists” that can be used to translate values during mappings.

Once defined, you can specify the Synonym Group to employ it in any relevant field mapping:

![](http://assets.toptal.io/uploads/blog/image/555/toptal-blog-image-1410442706635.png)

## Mappings based on value formatting and complex calculations

Values from one or more fields may need to be used to format a new value. For example, the source value may need decorating with constants `(e.g., sale.PriceEach = "$" + priceEach;)` or several fields may need to be used to generate a value `(e.g., sale.Code = code1 + “_” + code2;)`.

MetaDapper provides a formatting/templating capability that lets you build values using any of the fields in the current record, including substring portions of fields or constant values. After formatting, the value will be converted to the specified destination type (which, incidentally, does not need to be a string).

Similarly, complex calculations can be performed during mappings, employing a full set of mathematical operators and functions on any combination of field values and constants.

## Validation rules

Custom validation delegates can be registered and used in mappings. Here’s an example of a custom method to validate that a field value is an integer (without making the data type for the field an integer):

    private static bool ValidateIsInteger(
    Log log, CultureInfo cultureInfo, object value, ref List<ErrorInfo> errors)
    {
        try
        {
            Convert.ToInt32(value);
        }
        catch (Exception)
        {
            return false;
        }
    
        return true;
    }
    

The method would be registered when instantiating MetaDapper. Then it could be easily applied in any Field Mapping Definition:

![](http://assets.toptal.io/uploads/blog/image/556/toptal-blog-image-1410442821281.png)

## Grouping, Sorting, and Filtering

Grouping and sorting operations can often be handled in a database query but not all data sources are databases. MetaDapper therefore supports configuration of complex grouping and sorting operations that can be performed in-memory.

In cases where only a portion of the source data may be needed, filtering from non-database sources can be very complex to implement and maintain. MetaDapper supports configuring complex filters with Boolean operators for any number of field evaluations per record, with arbitrarily deep nesting of operations as needed. For example:

![](http://assets.toptal.io/uploads/blog/image/557/toptal-blog-image-1410443088165.png)

## Nested mappings

Some mappings require multiple passes to complete the data conversion process. Some examples include data that requires prefix or summation records, data that needs to be mapped differently depending on field values or document structure, or simply to isolate different stages of a complex mapping (i.e. translate names, type conversions, etc.). Toward that end, MetaDapper supports nested mappings to any level of depth.

## Format vs. structure

As a data mapping and conversion tool, MetaDapper is constructed to allow virtually any data format to be read or written to using internal reader and writer interfaces. This allows the creation of reader/writer classes that are extremely light weight and focused on the format-specific nuances only.

Readers and writers also behave as intelligently and flexibly as possible. For example, the XML reader and writer employ XPaths to specify where to retrieve or write data to in an XML file. The same configuration can also be used to read and write, for example, from non-XML formats (such as CSV files) in which case the XPath values will simply be ignored. Likewise, if a configuration that doesn’t include XPath settings is used with an XML reader or writer, an error will be generated.

## Yeah. Right. Sure. (Some Real Data Mapping Examples)

You’re skeptical. And I don’t blame you. Software tools are rarely all they claim to be. So here are a few real world examples where MetaDapper has already been used to provide operational benefit.

A company that provides medical insurance management software had customers that didn’t want to fill out web forms but wanted to provide their data in spreadsheets. Using MetaDapper, uploaded spreadsheets are read into memory, data cleaned, records validated and the results stored in their database. They’re able to accept Excel files from their customers without any human validation using MetaDapper with an easy to create configuration file for each spreadsheet template they publish.

A large gas company has an internal application and wanted their management users to be able to download reports in Excel format. The report formats would likely be regularly changed. MetaDapper facilitated Excel sheets to be generated from their database. Updating the Excel formats only required updating the MetaDapper configuration files without any code change or recompiling.

A company that provides asset management software needed a solution for generating financial data in customer dependent accounting package formats for import into those systems. A generic accounting data query was developed using an ORM wrapper and MetaDapper was used to sort, filter and map data into the desired schema and format for each customer. One or more MetaDapper configurations are made for each customer and this has become a major selling feature for new customers. The product can be configured (using MetaDapper) in minutes to support whatever custom or standard accounting package format so integration with essential and existing systems is included with each new sale. The same company uses MetaDapper in various software integration projects, mapping and converting data and converting internal codes between their systems.

A major auto reseller needed to add some sales reports in Excel format to one of their applications. The reports were added to the application in less than an hour – start to finish.

A developer needed a table of U.S. States identical to the set used on another website. MetaDapper was used to mine the data from the site and generate a SQL script for populating his table in a few minutes.

These are just a few examples of MetaDapper’s proven utility and value as a data mapping tool.

## Wrap-up

It takes a mental jump to start thinking about data conversion more generically and to start thinking about sets of data with business rules and unbounded usefulness. MetaDapper is a framework that fosters and facilitates that perspective.

Whether you use MetaDapper, another technology, or roll your own data mapping solutions, this has been an introduction to some of the complexity and hidden costs in data conversion projects. I hope you find it informative.

(For more information on MetaDapper, contact the MetaDapper team at info@metadapper.com.)

This article was originally published in [Toptal](http://www.toptal.com/data-science/)