---
id: 1024
title: Google Web Fonts
date: 2012-09-24T12:10:56+00:00
author: Sam Matthews
layout: page
guid: http://giscollective.org/?page_id=1024
---
Sick of using the standard web-safe fonts programmed into your browser? So are we. There&#8217;s a few different ways to tackle bringing in your own typeface for a website, but this one is the simplest so far. Google has a whole server of web fonts out there, which you can freely choose, link, and use. You&#8217;ll find there 500+ fonts cross the board in style but all integrate in a simple, quick way. You&#8217;ll first find the font you&#8217;re interested in and &#8220;Add To Collection&#8221; – click &#8220;Quick Use&#8221; and you&#8217;ll find a page simply giving you the link to put into the _head_ of your HTML page.

The code for your HTML 

<head>
  will be:</p> 
  
  <div class="wp_syntax">
    <table>
      <tr>
        <td class="line_numbers">
          <pre>1
</pre>
        </td>
        
        <td class="code">
          <pre class="html" style="font-family:monospace;">&lt;link href='http://fonts.googleapis.com/&lt;strong&gt;YOUR_CHOSEN_FONT&lt;/strong&gt; rel='stylesheet' type='text/css'&gt;</pre>
        </td>
      </tr>
    </table>
  </div>
  
  <p>
    When you are using the specific typeface in your CSS, you&#8217;ll simply use the &#8216;font-family&#8217; call and paste what google gives you as an integration code. For example:
  </p>
  
  <div class="wp_syntax">
    <table>
      <tr>
        <td class="line_numbers">
          <pre>1
2
3
</pre>
        </td>
        
        <td class="code">
          <pre class="css" style="font-family:monospace;"><span style="color: #cc00cc;">#full</span> <span style="color: #00AA00;">&#123;</span>
    <span style="color: #000000; font-weight: bold;">font-family</span><span style="color: #00AA00;">:</span> <span style="color: #ff0000;">'Source Code Pro'</span><span style="color: #00AA00;">,</span> <span style="color: #993333;">sans-serif</span><span style="color: #00AA00;">;</span>
<span style="color: #00AA00;">&#125;</span></pre>
        </td>
      </tr>
    </table>
  </div>
  
  <p>
    There you have it! Simple fonts. Pretty web pages.
  </p>