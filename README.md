## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/gelsbern/wowpages/edit/main/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/gelsbern/wowpages/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.

<body>

<div id="header">
<h1>Patchwerk Hateful Strike Calculator</h1>
</div>

<div id="content">
<div id="text"></div>

<ul>
<li>Base Armor <input id="armor" value="9500"/></li>
<li>Block <input id="block" value="0"/></li>
<li><input id="stance" type="checkbox"/> Defensive Stance</li>
<li><input id="stoneshield" type="checkbox"/> Greater Stoneshield Potion</li>
<li><input id="inspiration" type="checkbox"/> Inspiration / Ancestral Healing</li>
<li><input id="recalc" type="button" value="Calculate" onclick="Calculate()"></li>
</ul>
<div id="output">&nbsp;</div>
		
		
	
</div>

<script>
var _____WB$wombat$assign$function_____ = function(name) {return (self._wb_wombat && self._wb_wombat.local_init && self._wb_wombat.local_init(name)) || self[name]; };
if (!self.__WB_pmw) { self.__WB_pmw = function(obj) { this.__WB_source = obj; return this; } }
{
  let window = _____WB$wombat$assign$function_____("window");
  let self = _____WB$wombat$assign$function_____("self");
  let document = _____WB$wombat$assign$function_____("document");
  let location = _____WB$wombat$assign$function_____("location");
  let top = _____WB$wombat$assign$function_____("top");
  let parent = _____WB$wombat$assign$function_____("parent");
  let frames = _____WB$wombat$assign$function_____("frames");
  let opener = _____WB$wombat$assign$function_____("opener");

function GetDamageDone(stats, damage)
{
   var armor = stats.armor;

   if (stats.stoneshield) armor += 2000;
   if (stats.inspiration) armor *= 1.25;

   var mitigated = 1 - armor / (armor + 5755);

   if (mitigated < 0.25) mitigated = 0.25;
   damage = damage * mitigated;

   if (stats.stance) damage *= 0.9;

   damage -= stats.block;

   if (damage < 0) damage = 0;

   return damage;
}

function Calculate()
{
   stats = {
      armor:parseFloat(document.getElementById("armor").value),
      block:parseFloat(document.getElementById("block").value),
      stance:document.getElementById("stance").checked,
      stoneshield:document.getElementById("stoneshield").checked,
      inspiration:document.getElementById("inspiration").checked
   };
   var damage;
   var outstr;

   outstr = "<ul>\n";
   outstr += "<li>Maximum Damage = " + String(GetDamageDone(stats, 29900)) + "</li>\n";
   outstr += "<li>Minimum Damage = " + String(GetDamageDone(stats, 22100)) + "</li>\n";
   outstr += "</ul>";

   document.getElementById("output").innerHTML = outstr;
}

}
</script>


</body>
</html>	

