
<div id="header">
<h1>Patchwerk Hateful Strike Calculator</h1>
</div>

<div id="content">
<div id="text"></div>
	
&#8226; Hateful Strike hits the person in range with the most hitpoints primed by aggro. (It will hit a rogue if your tanks aren't healed up fast enough).<br><br>
&#8226; Hateful Strike hits for between 22100 and 29900 damage before mitigation (= avg 26000 non-mitigated damage). This means it is roughly 7500 average damage after mitigation on tier-2 warriors. The maximum hit will deal 29900*(damage modifier by armor); this means that, with 70% damage reduction, for example, a tank needs 29900*30%=8970 HP at all times.<br><br>
&#8226; Hateful Strike can never crit or be a crushing blow.<br><br>
&#8226; Hateful Strike hits roughly every 1.2 seconds.<br><br>
&#8226; Hateful Strike does NOT try to reapply upon a dodge/parry/miss. This is a common misconception (if the person with the highest health dodges/etc. and nobody else has been healed to higher health, then the same person will also take the next HS, which leads to this misconception). This means that dodge/parry is extremely important because it gives healers 1.2 more seconds to top off tanks.<br><br>
<br><br>
This fight will generally require your Hateful Strike tanks to be buffed using Flasks of the Titans and Stoneshield Potions and possibly to be specced in Protection.
<br><br>
If a druid must be used for Hateful Strikes, they should have close to 75% damage mitigation or more, plenty of stamina gear, and an appropriate spec.
<br><br>
Use the Hateful Strike Damage Calculator to determine if your tanks are geared with sufficient armor and hit points to survive Hateful Strikes.
<br><br>
Base Armor <input id="armor" value="9500"/><br>
Block <input id="block" value="0"/><br>
<input id="stance" type="checkbox"/> Defensive Stance<br>
<input id="stoneshield" type="checkbox"/> Greater Stoneshield Potion<br>
<input id="inspiration" type="checkbox"/> Inspiration / Ancestral Healing<br>
<input id="recalc" type="button" value="Calculate" onclick="Calculate()">
<br><br>
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

   outstr = "\n";
   outstr += "Maximum Damage = " + String(GetDamageDone(stats, 29900)) + "<br>\n";
   outstr += "Minimum Damage = " + String(GetDamageDone(stats, 22100)) + "<br>\n";
   
   document.getElementById("output").innerHTML = outstr;
}

}
</script>




