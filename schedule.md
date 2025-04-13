---
title: Scheduling Success Probability
description: Probability of finding a suitable time for a meeting
layout: default
---

<script src="https://cdn.jsdelivr.net/npm/chart.js" defer></script>

Number of options (potential timeslots): <span id="l">10</span>

<input type="range" min="1" max="100" value="10" class="slider" id="slots">

Number of required attendees: <span id="m">5</span>

<input type="range" min="1" max="20" value="5" class="slider" id="respondents">

Average number of timeslot conflicts (rejections) per required attendee: <span id="r">3</span>

<input type="range" min="0" max="100" value="3" class="slider" id="conflicts">

**Probability of finding a suitable time: <span id="probability"></span>%**

<div><canvas id="barChart"></canvas></div>

<a id="link" href=".">Permalink to result</a>.

{{ site.comments }}

> Based on *Brown, Mathur, Narayan "Scheduling meetings: are the odds in your favo[u]r?"* [*Eur. Phys. J. B 97 (120) 2024*](https://doi.org/10.1140/epjb/s10051-024-00742-z)

<script>
var l = document.getElementById("slots");
var m = document.getElementById("respondents");
var r = document.getElementById("conflicts");
var p = document.getElementById("probability");
// Set default values from URL parameters
var matches = /l=([0-9]+)/.exec(window.location.search);
l.value = matches ? parseInt(matches[1]) : 10;
matches = /m=([0-9]+)/.exec(window.location.search);
m.value = matches ? parseInt(matches[1]) : 5;
matches = /r=([0-9]+)/.exec(window.location.search);
r.value = matches ? parseInt(matches[1]) : 3;

function fact(n, base=0) {
  return n > base ? BigInt(n) * fact(n - 1, base) : 1n;
}
function gcd(a, b) {
  if (!b) return a;
  return gcd(b, a % b);
}
function bigDiv(a, b) {
  divisor = gcd(a, b);
  a /= divisor;
  b /= divisor;
  return Number(a / b) + Number(a % b) / Number(b);
}
function getProb(l, m, r, g) {
  // g: number of conflicts
  var prob = 0;
  for (var j = 0; j <= l - r - g; j++) {
    prob += Math.pow(-1, j) * bigDiv(fact(l, l - g - j), fact(j) * fact(g)) * Math.pow(
      bigDiv(fact(l - g - j, l - r - g - j), fact(l, l - r)),
      m
    );
  }
  return prob;
}
// wait for chart.js
document.addEventListener("DOMContentLoaded", () => {
  var chart = new Chart(document.getElementById('barChart'), {
    type: 'bar',
    data: {
      labels: Array.from({length: l.value}, (_, g) => g),
      datasets: [{
        label: "Probability (y-axis) of number of conflicts (x-axis)",
        data: Array.from({length: l.value}, (_, g) => 0)}]},
    options: {
      scales: {y: {beginAtZero: true, min: 0, max: 100}}}});
  function update() {
    document.getElementById("l").innerHTML = l.value;
    document.getElementById("m").innerHTML = m.value;
    document.getElementById("r").innerHTML = r.value;
    r.max = l.value;
    chart.data.labels = Array.from({length: l.value}, (_, g) => g);
    chart.data.datasets[0].data = Array.from({length: l.value}, (_, g) => {
      return getProb(l.value, m.value, r.value, g) * 100;
    });
    chart.update();
    p.innerHTML = Math.round(100 * (1 - getProb(l.value, m.value, r.value, 0)));
    document.getElementById("link").href = "./?l=" + l.value + "&m=" + m.value + "&r=" + r.value;
  }

  update();
  l.oninput = m.oninput = r.oninput = update;
});
</script>
