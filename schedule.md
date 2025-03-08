---
title: Scheduling Success Probability
description: Probability of finding a suitable time for a meeting
layout: default
---

Number of options (potential timeslots): <span id="l">10</span>

<input type="range" min="1" max="100" value="10" class="slider" id="slots">

Number of required attendees: <span id="m">5</span>

<input type="range" min="1" max="20" value="5" class="slider" id="respondents">

Average number of timeslot conflicts (rejections) per required attendee: <span id="r">3</span>

<input type="range" min="0" max="100" value="3" class="slider" id="conflicts">

**Probability of finding a suitable time: <span id="probability"></span>%**

<a id="link" href=".">Permalink to result</a>.

{{ site.comments }}

> Based on *Brown, Mathur, Narayan "Scheduling meetings: are the odds in your favo[u]r?"* [*Eur. Phys. J. B 97 (120) 2024*](https://doi.org/10.1140/epjb/s10051-024-00742-z)

<script type="text/javascript">
function factorial(n) {
  return n > 1 ? n * factorial(n - 1) : 1;
}
var l = document.getElementById("slots");
var m = document.getElementById("respondents");
var r = document.getElementById("conflicts");
var p = document.getElementById("probability");
function update() {
  document.getElementById("l").innerHTML = l.value;
  document.getElementById("m").innerHTML = m.value;
  document.getElementById("r").innerHTML = r.value;
  r.max = l.value;

  var J = l.value - r.value;
  var fail = 0;
  for (var j = 0; j <= J; j++) {
    fail += Math.pow(-1, j) * factorial(l.value) / factorial(j) / factorial(l.value - j) * Math.pow(
      factorial(J) * factorial(l.value - j) / factorial(l.value) / factorial(J - j),
      m.value
    );
  }
  p.innerHTML = Math.round(100 * (1 - fail));
  document.getElementById("link").href = "./?l=" + l.value + "&m=" + m.value + "&r=" + r.value;
}

var matches = /l=([0-9]+)/.exec(window.location.search);
l.value = matches ? parseInt(matches[1]) : 10;
matches = /m=([0-9]+)/.exec(window.location.search);
m.value = matches ? parseInt(matches[1]) : 5;
matches = /r=([0-9]+)/.exec(window.location.search);
r.value = matches ? parseInt(matches[1]) : 3;

update();
l.oninput = m.oninput = r.oninput = update;
</script>
