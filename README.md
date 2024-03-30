w
<h2>
 Selamat datang  
<img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="30px"/>
</h1>
<div align="center">
  <img src="https://media.giphy.com/media/dWesBcTLavkZuG35MI/giphy.gif" width="600" height="300"/>
</div>
<img align="center" src="https://github-readme-streak-stats.herokuapp.com?user=timcreative&theme=vue-dark&hide_border=true&date_format=M%20j%5B%2C%20Y%5D" alt="My github stats" />

<img align="center" src="https://github-readme-stats.vercel.app/api?username=timcreative&show_icons=true&include_all_commits=true&theme=cobalt&hide_border=true" alt="My github stats" /> 

<img align="center" src="https://github-readme-stats.vercel.app/api/top-langs/?username=timcreative&layout=compact&theme=cobalt&hide_border=true" />


Doa Mensyukuri Ni'mat

رَبِّ أَوْزِعْنِىٓ أَنْ أَشْكُرَ نِعْمَتَكَ ٱلَّتِىٓ أَنْعَمْتَ عَلَىَّ وَعَلَىٰ وَٰلِدَىَّ وَأَنْ أَعْمَلَ صَٰلِحًا تَرْضَىٰهُ وَأَدْخِلْنِى بِرَحْمَتِكَ فِى عِبَادِكَ ٱلصَّٰلِحِينَ


 
Ya Tuhanku, berilah aku ilham untuk tetap mensyukuri nikmat-Mu yang telah Engkau anugerahkan kepadaku dan kepada kedua orang ibu-bapakku dan untuk mengerjakan amal shalih yang Engkau ridhai, serta masukkanlah aku dengan rahmat-Mu ke dalam golongan hamba-hamba-Mu yang shalih


QS. Al-Naml 19


Keterangan :



Dijelaskan dalam Al-Qr'an bahwa ayat ini adalah doa Nabi Sulaiman kepada Allah SWT agar mendapatkan ilham untuk mensyukuri nikmat serta dimasukkan ke dalam golongan orang-orang yang beramal shalih di dunia hingga kemudian mendapatkan kebahagiaan di dunia dan akhirat.


In the GitHub file editor, replace the README.md file content with the following code:

<div id="header" align="center">
  <img src="https://media.giphy.com/media/M9gbBd9nbDrOTu1Mqx/giphy.gif" width="100"/>
</div>
The src attribute points to the URL we copied in the previous step. Since all the contents in this section are center-aligned, we’ve wrapped the image in an HTML div tag with the align="center" attribute.

Note: GitHub converts the README Markdown to HTML and renders it on GitHub. After conversion, the HTML is sanitized, and for security reasons, it ignores certain HTML tags and attributes such as <script>, <style>, style etc. For this reason, we’ve used an align attribute instead of CSS.

Now go to the preview tab. Pictured below is the output we get.

GIF preview
Next, we’ll add social network badges. On clicking the badge, it will redirect to the respective social networking sites. You can add social badges of various websites like Instagram, Facebook, Twitter, etc. For this tutorial, we’ll add three: Twitter, YouTube and LinkedIn.

To get the respective badges for each social network, we’ll use Shields.io, which provides various endpoints letting users create and customize social badges. We’ll use the https://img.shields.io/badge/ URL and pass additional parameters to this URL to get the respective social badges.

The first parameter we’ll pass is of the following format:

Label-Color
Label is the social network site name shown on the badge.
Color is the color of the badge.

For the three social networks, the values for this parameter will be:

LinkedIn: LinkedIn-blue
Twitter: Twitter-blue
YouTube: YouTube-red
When combined with https://img.shields.io/badge/, the following URL is created for LinkedIn:

https://img.shields.io/badge/LinkedIn-blue
After entering the above URL in the browser, we get the following output:

Linkedin badge with no styling
Note that we don’t have the icon for the badge added yet. To add it, we’ll use two query parameters in the following format:

logo={your social network icon name}
logoColor={color of the icon}
We’ll add both the parameters to the URL as below:

https://img.shields.io/badge/LinkedIn-blue?logo=linkedin&logoColor=white
We’ll also add a style parameter to the above URL. There are various styling options available, the details of which you can find at Shields.io. We’ll use for-the-badge styling.

The final URL for LinkedIn will be:

https://img.shields.io/badge/LinkedIn-blue?logo=linkedin&logoColor=white&style=for-the-badge
Now, when we hit this URL in the browser, we get the output pictured below.

Linkedin badge with styling
Similarly, we create URLs for other badges:

https://img.shields.io/badge/YouTube-red?style=for-the-badge&logo=youtube&logoColor=white
https://img.shields.io/badge/Twitter-blue?style=for-the-badge&logo=twitter&logoColor=white
We’ll wrap each URL in img tag like so:

<div id="badges">
  <img src="https://img.shields.io/badge/LinkedIn-blue?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn Badge"/>
  <img src="https://img.shields.io/badge/YouTube-red?style=for-the-badge&logo=youtube&logoColor=white" alt="Youtube Badge"/>
  <img src="https://img.shields.io/badge/Twitter-blue?style=for-the-badge&logo=twitter&logoColor=white" alt="Twitter Badge"/>
</div>
We’ve wrapped the images in <div> tags to make sure all badges come on a single line. The above code will only display the image generated from the URL. To add hyperlinks for each of the badges, we’ll wrap each image with an <a> tag.

Add the below code inside the <div> tag with id="header" and after the GIF <img> tag. Make sure to change the href attribute to point to your social profiles:

<div id="badges">
  <a href="your-linkedin-URL">
    <img src="https://img.shields.io/badge/LinkedIn-blue?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn Badge"/>
  </a>
  <a href="your-youtube-URL">
    <img src="https://img.shields.io/badge/YouTube-red?style=for-the-badge&logo=youtube&logoColor=white" alt="Youtube Badge"/>
  </a>
  <a href="your-twitter-URL">
    <img src="https://img.shields.io/badge/Twitter-blue?style=for-the-badge&logo=twitter&logoColor=white" alt="Twitter Badge"/>
  </a>
</div>
Pictured below is the output we get.

