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
