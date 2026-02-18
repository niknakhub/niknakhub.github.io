---
layout: page
title: MinPrepping - 72 Timer
permalink: /prepping/
---

<script src="https://cdn.tailwindcss.com"></script>

<div class="prepping-wrapper bg-white p-6 rounded-xl shadow-lg border border-green-100">
    <!-- HERO -->
    <div class="text-center py-8">
        <h1 class="text-3xl font-bold text-green-900 mb-4" data-i18n="hero_title">3 døgn. Det er alt, du behøver.</h1>
        <p class="text-gray-600 max-w-md mx-auto" data-i18n="hero_sub">Beredskab uden panik. Fokus på ro, orden og pladsbesparelse.</p>
    </div>

    <!-- BEREGNER (AUTOMATISERET AF AGENTERNE) -->
    <div class="bg-green-900 text-white p-8 rounded-2xl my-8">
        <h2 class="text-xl font-bold text-center mb-6" data-i18n="calc_title">Beredskabsberegner</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-8">
            <div>
                <label class="block text-xs font-bold uppercase mb-2 text-green-200" data-i18n="label_adult">Voksne</label>
                <input type="number" id="voksne" value="1" min="1" oninput="calculate()" class="w-full bg-white text-gray-800 p-3 rounded-lg border-none outline-none">
            </div>
            <div>
                <label class="block text-xs font-bold uppercase mb-2 text-green-200" data-i18n="label_child">Børn</label>
                <input type="number" id="children" value="0" min="0" oninput="calculate()" class="w-full bg-white text-gray-800 p-3 rounded-lg border-none outline-none">
            </div>
            <div>
                <label class="block text-xs font-bold uppercase mb-2 text-green-200" data-i18n="label_pet">Kæledyr</label>
                <input type="number" id="pets" value="0" min="0" oninput="calculate()" class="w-full bg-white text-gray-800 p-3 rounded-lg border-none outline-none">
            </div>
        </div>
        <div class="flex justify-around border-t border-green-800 pt-6 text-center">
            <div><p class="text-xs uppercase text-green-300" data-i18n="res_water">Vand (3 døgn)</p><p class="text-3xl font-bold text-white"><span id="waterRes">9</span> L</p></div>
            <div><p class="text-xs uppercase text-green-300" data-i18n="res_space">Plads-estimat</p><p class="text-lg font-bold text-white" id="spaceRes">Single-æske (15L)</p></div>
        </div>
    </div>
</div>

<script>
    // JS LOGIK (SAMLET)
    let currentLang = 'da';
    const translations = {
        da: { hero_title: "3 døgn. Det er alt, du behøver.", hero_sub: "Beredskab uden panik. Fokus på ro, orden og pladsbesparelse.", calc_title: "Beredskabsberegner", label_adult: "Voksne", label_child: "Børn", label_pet: "Kæledyr", res_water: "Vand (3 døgn)", res_space: "Plads-estimat", box_single: "Single-æske (15L)", box_house: "Familie-kasse (60L)" },
        en: { hero_title: "3 Days. That's all.", hero_sub: "Emergency prep without panic. Focus on calm and space-saving.", calc_title: "Prep Calculator", label_adult: "Adults", label_child: "Children", label_pet: "Pets", res_water: "Water (3 Days)", res_space: "Space Estimate", box_single: "Compact Box (15L)", box_house: "Family Crate (60L)" }
    };
    function calculate() {
        const v = parseInt(document.getElementById('voksne').value) || 0;
        const c = parseInt(document.getElementById('children').value) || 0;
        const p = parseInt(document.getElementById('pets').value) || 0;
        document.getElementById('waterRes').innerText = ((v + c) * 9) + (p * 3);
        document.getElementById('spaceRes').innerText = (v + c) > 1 ? translations[currentLang].box_house : translations[currentLang].box_single;
    }
</script>
