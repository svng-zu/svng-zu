import feedparser, datetime

feed = feedparser.parse("http://dxdata.tistory.com/rss")

#README 양식
markdown_text = """
###  🐱 github stats  

<div id="main" align="center">
    <img src="https://github-readme-stats.vercel.app/api?username=peterica&amp;count_private=true&amp;show_icons=true&amp;theme=radical"
        style="height: auto; margin-left: 20px; margin-right: 20px; padding: 10px;"/>
<!--         &lt;img src="https://github-readme-stats.vercel.app/api/top-langs/?username=qpyu66&amp;layout=compact"   
        style="height: auto; margin-left: 20px; margin-right: 20px; padding: 10px;"/>  -->
</div>

###  💁‍♀️ About Me  
<p align="center">
    <a href="https://dxdata.tistory.com/"><img src="https://img.shields.io/badge/Blog-FF5722?style=flat-square&amp;logo=Blogger&amp;logoColor=white"/></a>
    <a href="mailto:zztisdudoo@gmail.com"><img src="https://img.shields.io/badge/Gmail-d14836?style=flat-square&amp;logo=Gmail&amp;logoColor=white&amp;link=zztisdudoo@gmail.com"/></a>
</p>;

<br>

### 📕 Latest Blog Posts   

""" # list of blog posts will be appended here

for i in feed['entries'][:5]:
  # date = datetime.datetime.strptime(i['published'], "%a, %d %b %Y %H:%M:%S %z").strftime("%Y.%m.%d %H:%M")
  # print(date, i['link'], i['title'])
  markdown_text += f"<a href =\"{i['link']}\"> {i['title']} </a> <br>"

f = open("README.md", mode ="w", encoding="utf-8")
f.write(markdown_text)
f.close()