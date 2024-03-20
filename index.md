<html>
<body>

<h2>JavaScript Madness</h2>

<p>
Welcome!  This is a weighted-probability simulator of this year's March Madness tournament.  The way it works is you input what weights you'd like various metrics to hold below, which spits out a weighted, relative value score between (0 and 1) for each team.  From there, a formula that was constructed completely based on vibes/what generally looked reasonable (I am not a math guy sorry) produces a weighted probability of victory in each game.  From there, the simulator runs and produces a full bracket of results.  So, technically, anything can happen, including Texas Southern winning it all!--that's just extremely unlikely.  </br></br>
Note: I have basically never coded in JavaScript (where virtually all of this code is done), and have done no coding at all since a very basic web design class sophomore year in high school.  I did it in just a couple days, all original code, so please be gentle with your judgments.  It's just for fun! </br></br>

Here's a brief explainer of the weight options: </br>
	<b> Kenpom, BPI, EvanMiya, and Barthag/Torvik</b> are all computer metrics based on complicated algorithms I assume. </br>
	<b>Strength of Record</b> is ESPN's resume rating based on the likelihood of a team achieving their record. </br>
	<b>Win %</b> is, simply, a team's winning percentage.  Is it predictive?  Probably not!  But it <i> feels </i> like it is. </br>
	<b>Pure Chance</b> is what it sounds like.  I would recommend not putting this number higher than 1 or 2 in conjunction with the other values because it would quickly outweigh everything else.  If you put everything else at zero, and put pure chance at 1 (or any other number) the bracket will simulate as if every team has equal odds of winning every game.  Pure coin flip. </br></br>
	Recommendations: simplify the numbers, don't make them all super big, try to make them smaller where possible.  Ensure that you put a value into every input box (even if that value is zero).  <b> NOTE: You may need to press run more than once before it will actually run.  I do not know why.</b> </br>
	Happy Bracketing! </br>
choose your weights </br>
	kenpom: <input id="k" type="number"> </br>
	bpi: <input id="b" type="number"> </br>
	strength of record: <input id="sor" type="number"> </br>
	EvanMiya: <input id="sag" type="number"> </br>
	Barthag/Torvik: <input id="t" type="number"> </br>
	Win %: <input id="w" type="number"> </br>
	Pure Chance: <input id="c" type="number"> </br>
</p>

<button onclick="run()">run</button> 

<p id="demo"></p>

<script>

function run() {
function value(x1, x2, x3, x4, x5, x6) {
	return ((x1*k + x2*b + x3*sor + x4*sag + x5*t + x6*w + c*1)/(k*1 + b*1 + sor*1 + sag*1 + t*1 + w*1 + c*1))
}
function prob(p1, p2) {
	if ([((p1)/(p1 + p2))**(1 + (p1 - p2)*((p1 - p2)*4.8))] > 1e-6) {
		return [((p1)/(p1 + p2))**(1 + (p1 - p2)*((p1 - p2)*4.8))];
	} else {
		return 0;
}
}
var k;
k = document.getElementById("k").value;
var b;
b = document.getElementById("b").value;
var sor;
sor = document.getElementById("sor").value;
var sag;
sag = document.getElementById("sag").value;
var t;
t = document.getElementById("t").value;
var w;
w = document.getElementById("w").value;
var c;
c = document.getElementById("c").value;
const WestOne = {name: "UConn", kenpom: 1, bpi: 0.9133, sor: 0.9943, sag: 1, barthag: 0.9905, wins: 0.9842};
const WestSixteen = {name: "Stetson", kenpom: 0.1499, bpi: 0.2067, sor: 0.1714, sag: 0.161, barthag: 0.2001, wins: 0.4751};
const WestEight = {name: "FAU", kenpom: 0.6261, bpi: 0.61, sor: 0.7771, sag: 0.6546, barthag: 0.7931, wins: 0.6876};
const WestNine = {name: "Northwestern", kenpom: 0.61836, bpi: 0.5767, sor: 0.8514, sag: 0.5662, barthag: 0.8624, wins: 0.4928};
const WestFive = {name: "San Diego St.", kenpom: 0.7071, bpi: 0.6067, sor: 0.8343, sag: 0.6961, barthag: 0.872, wins: 0.5882};
const WestTwelve = {name: "UAB", kenpom: 0.3929, bpi: 0.3567, sor: 0.5314, sag: 0.3974, barthag: 0.5952, wins: 0.5317};
const WestFour = {name: "Auburn", kenpom: 0.9225, bpi: 0.8667, sor: 0.9486, sag: 0.9507, barthag: 0.9726, wins: 0.7579};
const WestThirteen = {name: "Yale", kenpom: 0.4676, bpi: 0.5, sor: 0.5429, sag: 0.5195, barthag: 0.6978, wins: 0.5955};
const WestSix = {name: "BYU", kenpom: 0.7378, bpi: 0.7033, sor: 0.8857, sag: 0.7221, barthag: 0.9074, wins: 0.5711};
const WestEleven = {name: "Duquesne", kenpom: 0.4652, bpi: 0.4367, sor: 0.5829, sag: 0.452, barthag: 0.7216, wins: 0.5495};
const WestThree = {name: "Illinois", kenpom: 0.8075, bpi: 0.7633, sor: 0.96, sag: 0.7922, barthag: 0.9274, wins: 0.7014};
const WestFourteen = {name: "Morehead St.", kenpom: 0.3739, bpi: 0.4133, sor: 0.3714, sag: 0.3429, barthag: 0.4992, wins: 0.7014};
const WestSeven = {name: "Washington St.", kenpom: 0.6256, bpi: 0.5633, sor: 0.8114, sag: 0.5922, barthag: 0.8419, wins: 0.6294};
const WestTen = {name: "Drake", kenpom: 0.5903, bpi: 0.5333, sor: 0.7657, sag: 0.5792, barthag: 0.8067, wins: 0.8145};
const WestTwo = {name: "Iowa St.", kenpom: 0.8715, bpi: 0.8467, sor: 0.9829, sag: 0.852, barthag: 0.9739, wins: 0.7579};
const WestFifteen = {name: "South Dakota St.", kenpom: 0.3159, bpi: 0.2733, sor: 0.1143, sag: 0.3481, barthag: 0.4929, wins: 0.4751};
const EastOne = {name: "North Carolina", kenpom: .823, bpi: .7767, sor: .9771, sag: .8364, barthag: .9381, wins: .7579};
const EastSixteena = {name: "Wagner", kenpom: 0.0096, bpi: 0.0567, sor: 0, sag: 0.0078, barthag: 0.051, wins: .2233};
const EastSixteenb = {name: "Howard", kenpom: 0.0525, bpi: 0.08, sor: 0, sag: 0.091, barthag: 0.1174, wins: .2489};
const EastEight = {name: "Mississippi St.", kenpom: .6668, bpi: .6233, sor: .7886, sag: .6597, barthag: .8698, wins: .4186};
const EastNine = {name: "Michigan St.", kenpom: .7148, bpi: .6867, sor: .7086, sag: .7351, barthag: .8969, wins: .338};
const EastFive = {name: "Saint Mary's", kenpom: .7115, bpi: .7167, sor: .7257, sag: .6623, barthag: .9244, wins: .7459};
const EastTwelve = {name: "Grand Canyon", kenpom: .5715, bpi: .52, sor: .72, sag: .5455, barthag: .7363, wins: .9207};
const EastFour = {name: "Alabama", kenpom: .7722, bpi: .78, sor: .92, sag: .7714, barthag: .915, wins: .4928};
const EastThirteen = {name: "Charleston", kenpom: .424, bpi: .4167, sor: .5771, sag: .4416, barthag: .6451, wins: .7579};
const EastSix = {name: "Clemson", kenpom: .6425, bpi: .6233, sor: .8057, sag: .6, barthag: .854, wins: .4928};
const EastEleven = {name: "New Mexico", kenpom: .6893, bpi: .5533, sor: .5914, sag: .6623, barthag: .8897, wins: .6593};
const EastThree = {name: "Baylor", kenpom: .768, bpi: .74, sor: .9543, sag: .761, barthag: .9122, wins: .5711};
const EastFourteen = {name: "Colgate", kenpom: .2962, bpi: .3733, sor: .3371, sag: .252, barthag: .402, wins: .6448};
const EastSeven = {name: "Dayton", kenpom: .6509, bpi: .6167, sor: .8629, sag: .5896, barthag: .8407, wins: .7196};
const EastTen = {name: "Nevada", kenpom: .6394, bpi: .53, sor: .8286, sag: .5896, barthag: .8407, wins: .7196};
const EastTwo = {name: "Arizona", kenpom: .8691, bpi: .85, sor: .9314, sag: .9013, barthag: .9667, wins: .6876};
const EastFifteen = {name: "Long Beach St.", kenpom: .2458, bpi: .22, sor: 0.1029, sag: .2494, barthag: .2972, wins: .3846};
const SouthOne = {name: "Houston", kenpom: 0.9885, bpi: 1, sor: 1, sag: .8987, barthag: 1, wins: .9276};
const SouthSixteen = {name: "Longwood", kenpom: 0.2683, bpi: 0.2933, sor: 0.04, sag: 0.2857, barthag: 0.3565, wins: .4186};
const SouthEight = {name: "Nebraska", kenpom: .6717, bpi: .6, sor: .8686, sag: .652, barthag: .8993, wins: .5711};
const SouthNine = {name: "Texas A&M", kenpom: .623, bpi: .6033, sor: .76, sag: .6156, barthag: .8348, wins: .362};
const SouthFive = {name: "Wisconsin", kenpom: .7282, bpi: .6867, sor: .8971, sag: .7169, barthag: .9012, wins: .43969842};
const SouthTwelve = {name: "James Madison", kenpom: .5479, bpi: .55, sor: .8171, sag: .5922, barthag: .7426, wins: .9842};
const SouthFour = {name: "Duke", kenpom: .8284, bpi: .8033, sor: .9143, sag: .8442, barthag: .934, wins: .6731};
const SouthThirteen = {name: "Vermont", kenpom: .4093, bpi: .45, sor: .6343, sag: .4338, barthag: .5895, wins: .8145};
const SouthSix = {name: "Texas Tech", kenpom: .6799, bpi: .6433, sor: .9086, sag: .6546, barthag: .8791, wins: .5711};
const SouthEleven = {name: "NC State", kenpom: .5516, bpi: .5267, sor: .6971, sag: .5429, barthag: .7684, wins: .406};
const SouthThree = {name: "Kentucky", kenpom: .7146, bpi: .67, sor: .8914, sag: .774, barthag: .8906, wins: .613};
const SouthFourteen = {name: "Oakland", kenpom: .3119, bpi: .31, sor: .4114, sag: .2753, barthag: .4953, wins: .5317};
const SouthSeven = {name: "Florida", kenpom: .4376, bpi: .64, sor: .9029, sag: .6546, barthag: .8926, wins: .5495};
const SouthTena = {name: "Boise St.", kenpom: .62936, bpi: .5467, sor: .6743, sag: .5636, barthag: .8398, wins: .5529};
const SouthTenb = {name: "Colorado", kenpom: .6783, bpi: .55, sor: .8, sag: .6442, barthag: .882, wins: .5882};
const SouthTwo = {name: "Marquette", kenpom: .7783, bpi: .74, sor: .9714, sag: .7818, barthag: .9412, wins: .6448};
const SouthFifteen = {name: "Western Kentucky", kenpom: .3173, bpi: 0.26, sor: 0.2057, sag: .361, barthag: .506, wins: .5128};
const MidwestOne = {name: "Purdue", kenpom: .9277, bpi: .89, sor: .9886, sag: .9377, barthag: .9818, wins: .9207};
const MidwestSixteena = {name: "Grambling St.", kenpom: 0.063, bpi: 0.0167, sor: 0, sag: .0156, barthag: 0.1034, wins: .1923};
const MidwestSixteenb = {name: "Montana St.", kenpom: 0.1545, bpi: 0.04, sor: 0, sag: .1507, barthag: 0.282, wins: .362};
const MidwestEight = {name: "Utah St.", kenpom: .5996, bpi: .49, sor: .8743, sag: .5143, barthag: .789, wins: .8042};
const MidwestNine = {name: "TCU", kenpom: .6507, bpi: .6333, sor: .8571, sag: .6312, barthag: .859, wins: .4545};
const MidwestFive = {name: "Gonzaga", kenpom: .7506, bpi: .7067, sor: .88, sag: .7818, barthag: .9184, wins: .7332};
const MidwestTwelve = {name: "McNeese St.", kenpom: .5469, bpi: .5367, sor: .6571, sag: .4909, barthag: .7104, wins: .979};
const MidwestFour = {name: "Kansas", kenpom: .6961, bpi: .6767, sor: .9371, sag: .7299, barthag: .9129, wins: .5529};
const MidwestThirteen = {name: "Samford", kenpom: .4751, bpi: .42, sor: .6057, sag: .4182, barthag: .6826, wins: .871};
const MidwestSix = {name: "South Carolina", kenpom: .5985, bpi: .53, sor: .9429, sag: .5325, barthag: .8242, wins: .7459};
const MidwestEleven = {name: "Oregon", kenpom: .5603, bpi: .52, sor: .7371, sag: .5247, barthag: .7898, wins: .5317};
const MidwestThree = {name: "Creighton", kenpom: .7937, bpi: .7833, sor: .9257, sag: .7948, barthag: .9364, wins: .613};
const MidwestFourteen = {name: "Akron", kenpom: .3615, bpi: .3933, sor: 0.4, sag: .3714, barthag: .5069, wins: .5882};
const MidwestSeven = {name: "Texas", kenpom: .6767, bpi: .65, sor: .8229, sag: .6831, barthag: .8998, wins: .4327};
const MidwestTena = {name: "Colorado St.", kenpom: .6345, bpi: .48, sor: .6857, sag: .5792, barthag: .8298, wins: .5882};
const MidwestTenb = {name: "Virginia", kenpom: .5287, bpi: .53, sor: .84, sag: .5169, barthag: .7892, wins: .5711};
const MidwestTwo = {name: "Tennessee", kenpom: .8539, bpi: .8267, sor: .9657, sag: .8909, barthag: .948, wins: .6731};
const MidwestFifteen = {name: "Saint Peters", kenpom: 0.1915, bpi: .18, sor: 0, sag: .1766, barthag: 0.2619, wins: .3726};


let W1n = WestOne.name;
let W1kp = WestOne.kenpom;
let W1bpi = WestOne.bpi;
let W1sor = WestOne.sor;
let W1sag = WestOne.sag;
let W1barthag = WestOne.barthag;
let W1wins = WestOne.wins;
let W1val = value(W1kp, W1bpi, W1sor, W1sag, W1barthag, W1wins);
let W16n = WestSixteen.name;
let W16kp = WestSixteen.kenpom;
let W16bpi = WestSixteen.bpi;
let W16sor = WestSixteen.sor;
let W16sag = WestSixteen.sag;
let W16barthag = WestSixteen.barthag;
let W16wins = WestSixteen.wins;
let W16val = value(W16kp, W16bpi, W16sor, W16sag, W16barthag, W16wins);
let W8n = WestEight.name;
let W8kp = WestEight.kenpom;
let W8bpi = WestEight.bpi;
let W8sor = WestEight.sor;
let W8sag = WestEight.sag;
let W8barthag = WestEight.barthag;
let W8wins = WestEight.wins;
let W8val = value(W8kp, W8bpi, W8sor, W8sag, W8barthag, W8wins);
let W9n = WestNine.name;
let W9kp = WestNine.kenpom;
let W9bpi = WestNine.bpi;
let W9sor = WestNine.sor;
let W9sag = WestNine.sag;
let W9barthag = WestNine.barthag;
let W9wins = WestNine.wins;
let W9val = value(W9kp, W9bpi, W9sor, W9sag, W9barthag, W9wins);
let W5n = WestFive.name;
let W5kp = WestFive.kenpom;
let W5bpi = WestFive.bpi;
let W5sor = WestFive.sor;
let W5sag = WestFive.sag;
let W5barthag = WestFive.barthag;
let W5wins = WestFive.wins;
let W5val = value(W5kp, W5bpi, W5sor, W5sag, W5barthag, W5wins);
let W12n = WestTwelve.name;
let W12kp = WestTwelve.kenpom;
let W12bpi = WestTwelve.bpi;
let W12sor = WestTwelve.sor;
let W12sag = WestTwelve.sag;
let W12barthag = WestTwelve.barthag;
let W12wins = WestTwelve.wins;
let W12val = value(W12kp, W12bpi, W12sor, W12sag, W12barthag, W12wins);
let W4n = WestFour.name;
let W4kp = WestFour.kenpom;
let W4bpi = WestFour.bpi;
let W4sor = WestFour.sor;
let W4sag = WestFour.sag;
let W4barthag = WestFour.barthag;
let W4wins = WestFour.wins;
let W4val = value(W4kp, W4bpi, W4sor, W4sag, W4barthag, W4wins);
let W13n = WestThirteen.name;
let W13kp = WestThirteen.kenpom;
let W13bpi = WestThirteen.bpi;
let W13sor = WestThirteen.sor;
let W13sag = WestThirteen.sag;
let W13barthag = WestThirteen.barthag;
let W13wins = WestThirteen.wins;
let W13val = value(W13kp, W13bpi, W13sor, W13sag, W13barthag, W13wins);
let W6n = WestSix.name;
let W6kp = WestSix.kenpom;
let W6bpi = WestSix.bpi;
let W6sor = WestSix.sor;
let W6sag = WestSix.sag;
let W6barthag = WestSix.barthag;
let W6wins = WestSix.wins;
let W6val = value(W6kp, W6bpi, W6sor, W6sag, W6barthag, W6wins);
let W11n = WestEleven.name;
let W11kp = WestEleven.kenpom;
let W11bpi = WestEleven.bpi;
let W11sor = WestEleven.sor;
let W11sag = WestEleven.sag;
let W11barthag = WestEleven.barthag;
let W11wins = WestEleven.wins;
let W11val = value(W11kp, W11bpi, W11sor, W11sag, W11barthag, W11wins);
let W3n = WestThree.name;
let W3kp = WestThree.kenpom;
let W3bpi = WestThree.bpi;
let W3sor = WestThree.sor;
let W3sag = WestThree.sag;
let W3barthag = WestThree.barthag;
let W3wins = WestThree.wins;
let W3val = value(W3kp, W3bpi, W3sor, W3sag, W3barthag, W3wins);
let W14n = WestFourteen.name;
let W14kp = WestFourteen.kenpom;
let W14bpi = WestFourteen.bpi;
let W14sor = WestFourteen.sor;
let W14sag = WestFourteen.sag;
let W14barthag = WestFourteen.barthag;
let W14wins = WestFourteen.wins;
let W14val = value(W14kp, W14bpi, W14sor, W14sag, W14barthag, W14wins);
let W7n = WestSeven.name;
let W7kp = WestSeven.kenpom;
let W7bpi = WestSeven.bpi;
let W7sor = WestSeven.sor;
let W7sag = WestSeven.sag;
let W7barthag = WestSeven.barthag;
let W7wins = WestSeven.wins;
let W7val = value(W7kp, W7bpi, W7sor, W7sag, W7barthag, W7wins);
let W10n = WestTen.name;
let W10kp = WestTen.kenpom;
let W10bpi = WestTen.bpi;
let W10sor = WestTen.sor;
let W10sag = WestTen.sag;
let W10barthag = WestTen.barthag;
let W10wins = WestTen.wins;
let W10val = value(W10kp, W10bpi, W10sor, W10sag, W10barthag, W10wins);
let W2n = WestTwo.name;
let W2kp = WestTwo.kenpom;
let W2bpi = WestTwo.bpi;
let W2sor = WestTwo.sor;
let W2sag = WestTwo.sag;
let W2barthag = WestTwo.barthag;
let W2wins = WestTwo.wins;
let W2val = value(W2kp, W2bpi, W2sor, W2sag, W2barthag, W2wins);
let W15n = WestFifteen.name;
let W15kp = WestFifteen.kenpom;
let W15bpi = WestFifteen.bpi;
let W15sor = WestFifteen.sor;
let W15sag = WestFifteen.sag;
let W15barthag = WestFifteen.barthag;
let W15wins = WestFifteen.wins;
let W15val = value(W15kp, W15bpi, W15sor, W15sag, W15barthag, W15wins);

let E1n = EastOne.name;
let E1kp = EastOne.kenpom;
let E1bpi = EastOne.bpi;
let E1sor = EastOne.sor;
let E1sag = EastOne.sag;
let E1barthag = EastOne.barthag;
let E1wins = EastOne.wins;
let E1val = value(E1kp, E1bpi, E1sor, E1sag, E1barthag, E1wins);
let E16an = EastSixteena.name;
let E16akp = EastSixteena.kenpom;
let E16abpi = EastSixteena.bpi;
let E16asor = EastSixteena.sor;
let E16asag = EastSixteena.sag;
let E16abarthag = EastSixteena.barthag;
let E16awins = EastSixteena.wins;
let E16aval = value(E16akp, E16abpi, E16asor, E16asag, E16abarthag, E16awins);
let E16bn = EastSixteenb.name;
let E16bkp = EastSixteenb.kenpom;
let E16bbpi = EastSixteenb.bpi;
let E16bsor = EastSixteenb.sor;
let E16bsag = EastSixteenb.sag;
let E16bbarthag = EastSixteenb.barthag;
let E16bwins = EastSixteenb.wins;
let E16bval = value(E16bkp, E16bbpi, E16bsor, E16bsag, E16bbarthag, E16bwins);
let E8n = EastEight.name;
let E8kp = EastEight.kenpom;
let E8bpi = EastEight.bpi;
let E8sor = EastEight.sor;
let E8sag = EastEight.sag;
let E8barthag = EastEight.barthag;
let E8wins = EastEight.wins;
let E8val = value(E8kp, E8bpi, E8sor, E8sag, E8barthag, E8wins);
let E9n = EastNine.name;
let E9kp = EastNine.kenpom;
let E9bpi = EastNine.bpi;
let E9sor = EastNine.sor;
let E9sag = EastNine.sag;
let E9barthag = EastNine.barthag;
let E9wins = EastNine.wins;
let E9val = value(E9kp, E9bpi, E9sor, E9sag, E9barthag, E9wins);
let E5n = EastFive.name;
let E5kp = EastFive.kenpom;
let E5bpi = EastFive.bpi;
let E5sor = EastFive.sor;
let E5sag = EastFive.sag;
let E5barthag = EastFive.barthag;
let E5wins = EastFive.wins;
let E5val = value(E5kp, E5bpi, E5sor, E5sag, E5barthag, E5wins);
let E12n = EastTwelve.name;
let E12kp = EastTwelve.kenpom;
let E12bpi = EastTwelve.bpi;
let E12sor = EastTwelve.sor;
let E12sag = EastTwelve.sag;
let E12barthag = EastTwelve.barthag;
let E12wins = EastTwelve.wins;
let E12val = value(E12kp, E12bpi, E12sor, E12sag, E12barthag, E12wins);
let E4n = EastFour.name;
let E4kp = EastFour.kenpom;
let E4bpi = EastFour.bpi;
let E4sor = EastFour.sor;
let E4sag = EastFour.sag;
let E4barthag = EastFour.barthag;
let E4wins = EastFour.wins;
let E4val = value(E4kp, E4bpi, E4sor, E4sag, E4barthag, E4wins);
let E13n = EastThirteen.name;
let E13kp = EastThirteen.kenpom;
let E13bpi = EastThirteen.bpi;
let E13sor = EastThirteen.sor;
let E13sag = EastThirteen.sag;
let E13barthag = EastThirteen.barthag;
let E13wins = EastThirteen.wins;
let E13val = value(E13kp, E13bpi, E13sor, E13sag, E13barthag, E13wins);
let E6n = EastSix.name;
let E6kp = EastSix.kenpom;
let E6bpi = EastSix.bpi;
let E6sor = EastSix.sor;
let E6sag = EastSix.sag;
let E6barthag = EastSix.barthag;
let E6wins = EastSix.wins;
let E6val = value(E6kp, E6bpi, E6sor, E6sag, E6barthag, E6wins);
let E11n = EastEleven.name;
let E11kp = EastEleven.kenpom;
let E11bpi = EastEleven.bpi;
let E11sor = EastEleven.sor;
let E11sag = EastEleven.sag;
let E11barthag = EastEleven.barthag;
let E11wins = EastEleven.wins;
let E11val = value(E11kp, E11bpi, E11sor, E11sag, E11barthag, E11wins);
let E3n = EastThree.name;
let E3kp = EastThree.kenpom;
let E3bpi = EastThree.bpi;
let E3sor = EastThree.sor;
let E3sag = EastThree.sag;
let E3barthag = EastThree.barthag;
let E3wins = EastThree.wins;
let E3val = value(E3kp, E3bpi, E3sor, E3sag, E3barthag, E3wins);
let E14n = EastFourteen.name;
let E14kp = EastFourteen.kenpom;
let E14bpi = EastFourteen.bpi;
let E14sor = EastFourteen.sor;
let E14sag = EastFourteen.sag;
let E14barthag = EastFourteen.barthag;
let E14wins = EastFourteen.wins;
let E14val = value(E14kp, E14bpi, E14sor, E14sag, E14barthag, E14wins);
let E7n = EastSeven.name;
let E7kp = EastSeven.kenpom;
let E7bpi = EastSeven.bpi;
let E7sor = EastSeven.sor;
let E7sag = EastSeven.sag;
let E7barthag = EastSeven.barthag;
let E7wins = EastSeven.wins;
let E7val = value(E7kp, E7bpi, E7sor, E7sag, E7barthag, E7wins);
let E10n = EastTen.name;
let E10kp = EastTen.kenpom;
let E10bpi = EastTen.bpi;
let E10sor = EastTen.sor;
let E10sag = EastTen.sag;
let E10barthag = EastTen.barthag;
let E10wins = EastTen.wins;
let E10val = value(E10kp, E10bpi, E10sor, E10sag, E10barthag, E10wins);
let E2n = EastTwo.name;
let E2kp = EastTwo.kenpom;
let E2bpi = EastTwo.bpi;
let E2sor = EastTwo.sor;
let E2sag = EastTwo.sag;
let E2barthag = EastTwo.barthag;
let E2wins = EastTwo.wins;
let E2val = value(E2kp, E2bpi, E2sor, E2sag, E2barthag, E2wins);
let E15n = EastFifteen.name;
let E15kp = EastFifteen.kenpom;
let E15bpi = EastFifteen.bpi;
let E15sor = EastFifteen.sor;
let E15sag = EastFifteen.sag;
let E15barthag = EastFifteen.barthag;
let E15wins = EastFifteen.wins;
let E15val = value(E15kp, E15bpi, E15sor, E15sag, E15barthag, E15wins);

let S1n = SouthOne.name;
let S1kp = SouthOne.kenpom;
let S1bpi = SouthOne.bpi;
let S1sor = SouthOne.sor;
let S1sag = SouthOne.sag;
let S1barthag = SouthOne.barthag;
let S1wins = SouthOne.wins;
let S1val = value(S1kp, S1bpi, S1sor, S1sag, S1barthag, S1wins);
let S16n = SouthSixteen.name;
let S16kp = SouthSixteen.kenpom;
let S16bpi = SouthSixteen.bpi;
let S16sor = SouthSixteen.sor;
let S16sag = SouthSixteen.sag;
let S16barthag = SouthSixteen.barthag;
let S16wins = SouthSixteen.wins;
let S16val = value(S16kp, S16bpi, S16sor, S16sag, S16barthag, S16wins);
let S8n = SouthEight.name;
let S8kp = SouthEight.kenpom;
let S8bpi = SouthEight.bpi;
let S8sor = SouthEight.sor;
let S8sag = SouthEight.sag;
let S8barthag = SouthEight.barthag;
let S8wins = SouthEight.wins;
let S8val = value(S8kp, S8bpi, S8sor, S8sag, S8barthag, S8wins);
let S9n = SouthNine.name;
let S9kp = SouthNine.kenpom;
let S9bpi = SouthNine.bpi;
let S9sor = SouthNine.sor;
let S9sag = SouthNine.sag;
let S9barthag = SouthNine.barthag;
let S9wins = SouthNine.wins;
let S9val = value(S9kp, S9bpi, S9sor, S9sag, S9barthag, S9wins);
let S5n = SouthFive.name;
let S5kp = SouthFive.kenpom;
let S5bpi = SouthFive.bpi;
let S5sor = SouthFive.sor;
let S5sag = SouthFive.sag;
let S5barthag = SouthFive.barthag;
let S5wins = SouthFive.wins;
let S5val = value(S5kp, S5bpi, S5sor, S5sag, S5barthag, S5wins);
let S12n = SouthTwelve.name;
let S12kp = SouthTwelve.kenpom;
let S12bpi = SouthTwelve.bpi;
let S12sor = SouthTwelve.sor;
let S12sag = SouthTwelve.sag;
let S12barthag = SouthTwelve.barthag;
let S12wins = SouthTwelve.wins;
let S12val = value(S12kp, S12bpi, S12sor, S12sag, S12barthag, S12wins);
let S4n = SouthFour.name;
let S4kp = SouthFour.kenpom;
let S4bpi = SouthFour.bpi;
let S4sor = SouthFour.sor;
let S4sag = SouthFour.sag;
let S4barthag = SouthFour.barthag;
let S4wins = SouthFour.wins;
let S4val = value(S4kp, S4bpi, S4sor, S4sag, S4barthag, S4wins);
let S13n = SouthThirteen.name;
let S13kp = SouthThirteen.kenpom;
let S13bpi = SouthThirteen.bpi;
let S13sor = SouthThirteen.sor;
let S13sag = SouthThirteen.sag;
let S13barthag = SouthThirteen.barthag;
let S13wins = SouthThirteen.wins;
let S13val = value(S13kp, S13bpi, S13sor, S13sag, S13barthag, S13wins);
let S6n = SouthSix.name;
let S6kp = SouthSix.kenpom;
let S6bpi = SouthSix.bpi;
let S6sor = SouthSix.sor;
let S6sag = SouthSix.sag;
let S6barthag = SouthSix.barthag;
let S6wins = SouthSix.wins;
let S6val = value(S6kp, S6bpi, S6sor, S6sag, S6barthag, S6wins);
let S11n = SouthEleven.name;
let S11kp = SouthEleven.kenpom;
let S11bpi = SouthEleven.bpi;
let S11sor = SouthEleven.sor;
let S11sag = SouthEleven.sag;
let S11barthag = SouthEleven.barthag;
let S11wins = SouthEleven.wins;
let S11val = value(S11kp, S11bpi, S11sor, S11sag, S11barthag, S11wins);
let S3n = SouthThree.name;
let S3kp = SouthThree.kenpom;
let S3bpi = SouthThree.bpi;
let S3sor = SouthThree.sor;
let S3sag = SouthThree.sag;
let S3barthag = SouthThree.barthag;
let S3wins = SouthThree.wins;
let S3val = value(S3kp, S3bpi, S3sor, S3sag, S3barthag, S3wins);
let S14n = SouthFourteen.name;
let S14kp = SouthFourteen.kenpom;
let S14bpi = SouthFourteen.bpi;
let S14sor = SouthFourteen.sor;
let S14sag = SouthFourteen.sag;
let S14barthag = SouthFourteen.barthag;
let S14wins = SouthFourteen.wins;
let S14val = value(S14kp, S14bpi, S14sor, S14sag, S14barthag, S14wins);
let S7n = SouthSeven.name;
let S7kp = SouthSeven.kenpom;
let S7bpi = SouthSeven.bpi;
let S7sor = SouthSeven.sor;
let S7sag = SouthSeven.sag;
let S7barthag = SouthSeven.barthag;
let S7wins = SouthSeven.wins;
let S7val = value(S7kp, S7bpi, S7sor, S7sag, S7barthag, S7wins);
let S10an = SouthTena.name;
let S10akp = SouthTena.kenpom;
let S10abpi = SouthTena.bpi;
let S10asor = SouthTena.sor;
let S10asag = SouthTena.sag;
let S10abarthag = SouthTena.barthag;
let S10awins = SouthTena.wins;
let S10aval = value(S10akp, S10abpi, S10asor, S10asag, S10abarthag, S10awins);
let S10bn = SouthTenb.name;
let S10bkp = SouthTenb.kenpom;
let S10bbpi = SouthTenb.bpi;
let S10bsor = SouthTenb.sor;
let S10bsag = SouthTenb.sag;
let S10bbarthag = SouthTenb.barthag;
let S10bwins = SouthTenb.wins;
let S10bval = value(S10bkp, S10bbpi, S10bsor, S10bsag, S10bbarthag, S10bwins);
let S2n = SouthTwo.name;
let S2kp = SouthTwo.kenpom;
let S2bpi = SouthTwo.bpi;
let S2sor = SouthTwo.sor;
let S2sag = SouthTwo.sag;
let S2barthag = SouthTwo.barthag;
let S2wins = SouthTwo.wins;
let S2val = value(S2kp, S2bpi, S2sor, S2sag, S2barthag, S2wins);
let S15n = SouthFifteen.name;
let S15kp = SouthFifteen.kenpom;
let S15bpi = SouthFifteen.bpi;
let S15sor = SouthFifteen.sor;
let S15sag = SouthFifteen.sag;
let S15barthag = SouthFifteen.barthag;
let S15wins = SouthFifteen.wins;
let S15val = value(S15kp, S15bpi, S15sor, S15sag, S15barthag, S15wins);

let MW1n = MidwestOne.name;
let MW1kp = MidwestOne.kenpom;
let MW1bpi = MidwestOne.bpi;
let MW1sor = MidwestOne.sor;
let MW1sag = MidwestOne.sag;
let MW1barthag = MidwestOne.barthag;
let MW1wins = MidwestOne.wins;
let MW1val = value(S1kp, MW1bpi, MW1sor, MW1sag, MW1barthag, MW1wins);
let MW16an = MidwestSixteena.name;
let MW16akp = MidwestSixteena.kenpom;
let MW16abpi = MidwestSixteena.bpi;
let MW16asor = MidwestSixteena.sor;
let MW16asag = MidwestSixteena.sag;
let MW16abarthag = MidwestSixteena.barthag;
let MW16awins = MidwestSixteena.wins;
let MW16aval = value(MW16akp, MW16abpi, MW16asor, MW16asag, MW16abarthag, MW16awins);
let MW16bn = MidwestSixteenb.name;
let MW16bkp = MidwestSixteenb.kenpom;
let MW16bbpi = MidwestSixteenb.bpi;
let MW16bsor = MidwestSixteenb.sor;
let MW16bsag = MidwestSixteenb.sag;
let MW16bbarthag = MidwestSixteenb.barthag;
let MW16bwins = MidwestSixteenb.wins;
let MW16bval = value(MW16bkp, MW16bbpi, MW16bsor, MW16bsag, MW16bbarthag, MW16bwins);
let MW8n = MidwestEight.name;
let MW8kp = MidwestEight.kenpom;
let MW8bpi = MidwestEight.bpi;
let MW8sor = MidwestEight.sor;
let MW8sag = MidwestEight.sag;
let MW8barthag = MidwestEight.barthag;
let MW8wins = MidwestEight.wins;
let MW8val = value(MW8kp, MW8bpi, MW8sor, MW8sag, MW8barthag, MW8wins);
let MW9n = MidwestNine.name;
let MW9kp = MidwestNine.kenpom;
let MW9bpi = MidwestNine.bpi;
let MW9sor = MidwestNine.sor;
let MW9sag = MidwestNine.sag;
let MW9barthag = MidwestNine.barthag;
let MW9wins = MidwestNine.wins;
let MW9val = value(MW9kp, MW9bpi, MW9sor, MW9sag, MW9barthag, MW9wins);
let MW5n = MidwestFive.name;
let MW5kp = MidwestFive.kenpom;
let MW5bpi = MidwestFive.bpi;
let MW5sor = MidwestFive.sor;
let MW5sag = MidwestFive.sag;
let MW5barthag = MidwestFive.barthag;
let MW5wins = MidwestFive.wins;
let MW5val = value(MW5kp, MW5bpi, MW5sor, MW5sag, MW5barthag, MW5wins);
let MW12n = MidwestTwelve.name;
let MW12kp = MidwestTwelve.kenpom;
let MW12bpi = MidwestTwelve.bpi;
let MW12sor = MidwestTwelve.sor;
let MW12sag = MidwestTwelve.sag;
let MW12barthag = MidwestTwelve.barthag;
let MW12wins = MidwestTwelve.wins;
let MW12val = value(MW12kp, MW12bpi, MW12sor, MW12sag, MW12barthag, MW12wins);
let MW4n = MidwestFour.name;
let MW4kp = MidwestFour.kenpom;
let MW4bpi = MidwestFour.bpi;
let MW4sor = MidwestFour.sor;
let MW4sag = MidwestFour.sag;
let MW4barthag = MidwestFour.barthag;
let MW4wins = MidwestFour.wins;
let MW4val = value(MW4kp, MW4bpi, MW4sor, MW4sag, MW4barthag, MW4wins);
let MW13n = MidwestThirteen.name;
let MW13kp = MidwestThirteen.kenpom;
let MW13bpi = MidwestThirteen.bpi;
let MW13sor = MidwestThirteen.sor;
let MW13sag = MidwestThirteen.sag;
let MW13barthag = MidwestThirteen.barthag;
let MW13wins = MidwestThirteen.wins;
let MW13val = value(MW13kp, MW13bpi, MW13sor, MW13sag, MW13barthag, MW13wins);
let MW6n = MidwestSix.name;
let MW6kp = MidwestSix.kenpom;
let MW6bpi = MidwestSix.bpi;
let MW6sor = MidwestSix.sor;
let MW6sag = MidwestSix.sag;
let MW6barthag = MidwestSix.barthag;
let MW6wins = MidwestSix.wins;
let MW6val = value(MW6kp, MW6bpi, MW6sor, MW6sag, MW6barthag, MW6wins);
let MW11n = MidwestEleven.name;
let MW11kp = MidwestEleven.kenpom;
let MW11bpi = MidwestEleven.bpi;
let MW11sor = MidwestEleven.sor;
let MW11sag = MidwestEleven.sag;
let MW11barthag = MidwestEleven.barthag;
let MW11wins = MidwestEleven.wins;
let MW11val = value(MW11kp, MW11bpi, MW11sor, MW11sag, MW11barthag, MW11wins);
let MW3n = MidwestThree.name;
let MW3kp = MidwestThree.kenpom;
let MW3bpi = MidwestThree.bpi;
let MW3sor = MidwestThree.sor;
let MW3sag = MidwestThree.sag;
let MW3barthag = MidwestThree.barthag;
let MW3wins = MidwestThree.wins;
let MW3val = value(MW3kp, MW3bpi, MW3sor, MW3sag, MW3barthag, MW3wins);
let MW14n = MidwestFourteen.name;
let MW14kp = MidwestFourteen.kenpom;
let MW14bpi = MidwestFourteen.bpi;
let MW14sor = MidwestFourteen.sor;
let MW14sag = MidwestFourteen.sag;
let MW14barthag = MidwestFourteen.barthag;
let MW14wins = MidwestFourteen.wins;
let MW14val = value(MW14kp, MW14bpi, MW14sor, MW14sag, MW14barthag, MW14wins);
let MW7n = MidwestSeven.name;
let MW7kp = MidwestSeven.kenpom;
let MW7bpi = MidwestSeven.bpi;
let MW7sor = MidwestSeven.sor;
let MW7sag = MidwestSeven.sag;
let MW7barthag = MidwestSeven.barthag;
let MW7wins = MidwestSeven.wins;
let MW7val = value(MW7kp, MW7bpi, MW7sor, MW7sag, MW7barthag, MW7wins);
let MW10an = MidwestTena.name;
let MW10akp = MidwestTena.kenpom;
let MW10abpi = MidwestTena.bpi;
let MW10asor = MidwestTena.sor;
let MW10asag = MidwestTena.sag;
let MW10abarthag = MidwestTena.barthag;
let MW10awins = MidwestTena.wins;
let MW10aval = value(MW10akp, MW10abpi, MW10asor, MW10asag, MW10abarthag, MW10awins);
let MW10bn = MidwestTenb.name;
let MW10bkp = MidwestTenb.kenpom;
let MW10bbpi = MidwestTenb.bpi;
let MW10bsor = MidwestTenb.sor;
let MW10bsag = MidwestTenb.sag;
let MW10bbarthag = MidwestTenb.barthag;
let MW10bwins = MidwestTenb.wins;
let MW10bval = value(MW10bkp, MW10bbpi, MW10bsor, MW10bsag, MW10bbarthag, MW10bwins);
let MW2n = MidwestTwo.name;
let MW2kp = MidwestTwo.kenpom;
let MW2bpi = MidwestTwo.bpi;
let MW2sor = MidwestTwo.sor;
let MW2sag = MidwestTwo.sag;
let MW2barthag = MidwestTwo.barthag;
let MW2wins = MidwestTwo.wins;
let MW2val = value(MW2kp, MW2bpi, MW2sor, MW2sag, MW2barthag, MW2wins);
let MW15n = MidwestFifteen.name;
let MW15kp = MidwestFifteen.kenpom;
let MW15bpi = MidwestFifteen.bpi;
let MW15sor = MidwestFifteen.sor;
let MW15sag = MidwestFifteen.sag;
let MW15barthag = MidwestFifteen.barthag;
let MW15wins = MidwestFifteen.wins;
let MW15val = value(MW15kp, MW15bpi, MW15sor, MW15sag, MW15barthag, MW15wins);


let rn1 = [Math.random()];
if (W1val < W16val) {
	var r1 = prob(W1val, W16val)
	if (r1 > rn1) {
	var winw116n = W1n;
	var winw116val = W1val;
	var lossw116n = W16n;
} else {
	var winw116n = W16n;
	var winw116val = W16val;
	var lossw116n = W1n;
}
} else {
	var r1 = prob(W16val, W1val)
	if (rn1 > r1) {
	var winw116n = W1n;
	var winw116val = W1val;
	var lossw116n = W16n;
} else {
	var winw116n = W16n;
	var winw116val = W16val;
	var lossw116n = W1n;
}
}
let rn2 = [Math.random()];
if (W8val < W9val) {
	var r2 = prob(W8val, W9val)
	if (r2 > rn2) {
	var winw89n = W8n;
	var winw89val = W8val;
	var lossw89n = W9n;
} else {
	var winw89n = W9n;
	var winw89val = W9val;
	var lossw89n = W8n;
}
} else {
	var r2 = prob(W9val, W8val)
	if (rn2 > r2) {
	var winw89n = W8n;
	var winw89val = W8val;
	var lossw89n = W9n;
} else {
	var winw89n = W9n;
	var winw89val = W9val;
	var lossw89n = W8n;
}
}
let rn3 = [Math.random()];
if (W5val < W12val) {
	var r3 = prob(W5val, W12val)
	if (r3 > rn3) {
	var winw512n = W5n;
	var winw512val = W5val;
	var lossw512n = W12n;
} else {
	var winw512n = W12n;
	var winw512val = W12val;
	var lossw512n = W5n;
}
} else {
	var r3 = prob(W12val, W5val)
	if (rn3 > r3) {
	var winw512n = W5n;
	var winw512val = W5val;
	var lossw512n = W12n;
} else {
	var winw512n = W12n;
	var winw512val = W12val;
	var lossw512n = W5n;
}
}
let rn4 = [Math.random()];
if (W4val < W13val) {
	var r4 = prob(W4val, W1val)
	if (r4 > rn4) {
	var winw413n = W4n;
	var winw413val = W4val;
	var lossw413n = W13n;
} else {
	var winw413n = W13n;
	var winw413val = W13val;
	var lossw413n = W4n;
}
} else {
	var r4 = prob(W13val, W4val)
	if (rn4 > r4) {
	var winw413n = W4n;
	var winw413val = W4val;
	var lossw413n = W13n;
} else {
	var winw413n = W13n;
	var winw413val = W13val;
	var lossw413n = W4n;
}
}
let rn5 = [Math.random()];
if (W6val < W11val) {
	var r5 = prob(W6val, W11val)
	if (r5 > rn5) {
	var winw611n = W6n;
	var winw611val = W6val;
	var lossw611n = W11n;
} else {
	var winw611n = W11n;
	var winw611val = W11val;
	var lossw611n = W6n;
}
} else {
	var r5 = prob(W11val, W6val)
	if (rn5 > r5) {
	var winw611n = W6n;
	var winw611val = W6val;
	var lossw611n = W11n;
} else {
	var winw611n = W11n;
	var winw611val = W11val;
	var lossw611n = W6n;
}
}
let rn6 = [Math.random()];
if (W3val < W14val) {
	var r6 = prob(W3val, W14val)
	if (r6 > rn6) {
	var winw314n = W3n;
	var winw314val = W3val;
	var lossw314n = W14n;
} else {
	var winw314n = W14n;
	var winw314val = W14val;
	var lossw314n = W3n;
}
} else {
	var r6 = prob(W14val, W3val)
	if (rn6 > r6) {
	var winw314n = W3n;
	var winw314val = W3val;
	var lossw314n = W14n;
} else {
	var winw314n = W14n;
	var winw314val = W14val;
	var lossw314n = W3n;
}
}
let rn7 = [Math.random()];
if (W7val < W10val) {
	var r7 = prob(W7val, W10val)
	if (r7 > rn7) {
	var winw710n = W7n;
	var winw710val = W7val;
	var lossw710n = W10n;
} else {
	var winw710n = W10n;
	var winw710val = W10val;
	var lossw710n = W7n;
}
} else {
	var r7 = prob(W10val, W7val)
	if (rn7 > r7) {
	var winw710n = W7n;
	var winw710val = W7val;
	var lossw710n = W10n;
} else {
	var winw710n = W10n;
	var winw710val = W10val;
	var lossw710n = W7n;
}
}
let rn8 = [Math.random()];
if (W2val < W15val) {
	var r8 = prob(W2val, W15val)
	if (r8 > rn8) {
	var winw215n = W2n;
	var winw215val = W2val;
	var lossw215n = W15n;
} else {
	var winw215n = W15n;
	var winw215val = W15val;
	var lossw215n = W2n;
}
} else {
	var r8 = prob(W15val, W2val)
	if (rn8 > r8) {
	var winw215n = W2n;
	var winw215val = W2val;
	var lossw215n = W15n;
} else {
	var winw215n = W15n;
	var winw215val = W15val;
	var lossw215n = W2n;
}
}
let rn9 = [Math.random()];
if (winw116val < winw89val) {
	var r9 = prob(winw116val, winw89val)
	if (r9 > rn9) {
	var winw18n = winw116n;
	var winw18val = winw116val;
	var lossw18n = winw89n;
} else {
	var winw18n = winw89n;
	var winw18val = winw89val;
	var lossw18n = winw116n;
}
} else {
	var r9 = prob(winw89val, winw116val)
	if (rn9 > r9) {
	var winw18n = winw116n;
	var winw18val = winw116val;
	var lossw18n = winw89n;
} else {
	var winw18n = winw89n;
	var winw18val = winw89val;
	var lossw18n = winw116n;
}
}
let rn10 = [Math.random()];
if (winw512val < winw413val) {
	var r10 = prob(winw512val, winw413val)
	if (r10 > rn10) {
	var winw45n = winw512n;
	var winw45val = winw512val;
	var lossw45n = winw413n;
} else {
	var winw45n = winw413n;
	var winw45val = winw413val;
	var lossw45n = winw512n;
}
} else {
	var r10 = prob(winw413val, winw512val)
	if (rn10 > r10) {
	var winw45n = winw512n;
	var winw45val = winw512val;
	var lossw45n = winw413n;
} else {
	var winw45n = winw413n;
	var winw45val = winw413val;
	var lossw45n = winw512n;
}
}
let rn11 = [Math.random()];
if (winw611val < winw314val) {
	var r11 = prob(winw611val, winw314val)
	if (r11 > rn11) {
	var winw36n = winw611n;
	var winw36val = winw611val;
	var lossw36n = winw314n;
} else {
	var winw36n = winw314n;
	var winw36val = winw314val;
	var lossw36n = winw611n;
}
} else {
	var r11 = prob(winw314val, winw611val)
	if (rn11 > r11) {
	var winw36n = winw611n;
	var winw36val = winw611val;
	var lossw36n = winw314n;
} else {
	var winw36n = winw314n;
	var winw36val = winw314val;
	var lossw36n = winw611n;
}
}
let rn12 = [Math.random()];
if (winw710val < winw215val) {
	var r12 = prob(winw710val, winw215val)
	if (r12 > rn12) {
	var winw27n = winw710n;
	var winw27val = winw710val;
	var lossw27n = winw215n;
} else {
	var winw27n = winw215n;
	var winw27val = winw215val;
	var lossw27n = winw710n;
}
} else {
	var r12 = prob(winw215val, winw710val)
	if (rn12 > r12) {
	var winw27n = winw710n;
	var winw27val = winw710val;
	var lossw27n = winw215n;
} else {
	var winw27n = winw215n;
	var winw27val = winw215val;
	var lossw27n = winw710n;
}
}

let rn13 = [Math.random()];
if (winw18val < winw45val) {
	var r13 = prob(winw18val, winw45val)
	if (r13 > rn13) {
	var winw14n = winw18n;
	var winw14val = winw18val;
	var lossw14n = winw45n;
} else {
	var winw14n = winw45n;
	var winw14val = winw45val;
	var lossw14n = winw18n;
}
} else {
	var r13 = prob(winw45val, winw18val)
	if (rn13 > r13) {
	var winw14n = winw18n;
	var winw14val = winw18val;
	var lossw14n = winw45n;
} else {
	var winw14n = winw45n;
	var winw14val = winw45val;
	var lossw14n = winw18n;
}
}
let rn14 = [Math.random()];
if (winw36val < winw27val) {
	var r14 = prob(winw36val, winw27val)
	if (r14 > rn14) {
	var winw23n = winw36n;
	var winw23val = winw36val;
	var lossw23n = winw27n;
} else {
	var winw23n = winw27n;
	var winw23val = winw27val;
	var lossw23n = winw36n;
}
} else {
	var r14 = prob(winw27val, winw36val)
	if (rn14 > r14) {
	var winw23n = winw36n;
	var winw23val = winw36val;
	var lossw23n = winw27n;
} else {
	var winw23n = winw27n;
	var winw23val = winw27val;
	var lossw23n = winw36n;
}
}
let rn15 = [Math.random()];
if (winw14val < winw23val) {
	var r15 = prob(winw14val, winw23val)
	if (r15 > rn15) {
	var winw12n = winw14n;
	var winw12val = winw14val;
	var lossw12n = winw23n;
} else {
	var winw12n = winw23n;
	var winw12val = winw23val;
	var lossw12n = winw14n;
}
} else {
	var r15 = prob(winw23val, winw14val)
	if (rn15 > r15) {
	var winw12n = winw14n;
	var winw12val = winw14val;
	var lossw12n = winw23n;
} else {
	var winw12n = winw23n;
	var winw12val = winw23val;
	var lossw12n = winw14n;
}
}

let rn0a = [Math.random()];
if (E16aval < E16bval) {
	var r0a = prob(E16aval, E16bval)
	if (r0a > rn0a) {
	var wineplayinn = E16an;
	var wineplayinval = E16aval;
	var losseplayinn = E16bn;
} else {
	var wineplayinn = E16bn;
	var wineplayinval = E16bval;
	var losseplayinn = E16an;
}
} else {
	var r0a = prob(E16bval, E16aval)
	if (rn0a > r0a) {
	var wineplayinn = E16an;
	var wineplayinval = E16aval;
	var losseplayinn = E16bn;
} else {
	var wineplayinn = E16bn;
	var wineplayinval = E16bval;
	var losseplayinn = E16an;
}
}

let rn16 = [Math.random()];
if (E1val < wineplayinval) {
	var r16 = prob(E1val, wineplayinval)
	if (r16 > rn16) {
	var wine116n = E1n;
	var wine116val = E1val;
	var losse116n = wineplayinn;
} else {
	var wine116n = wineplayinn;
	var wine116val = wineplayinval;
	var losse116n = E1n;
}
} else {
	var r16 = prob(wineplayinval, E1val)
	if (rn16 > r16) {
	var wine116n = E1n;
	var wine116val = E1val;
	var losse116n = wineplayinn;
} else {
	var wine116n = wineplayinn;
	var wine116val = wineplayinval;
	var losse116n = E1n;
}
}
let rn17 = [Math.random()];
if (E8val < E9val) {
	var r17 = prob(E8val, E9val)
	if (r17 > rn17) {
	var wine89n = E8n;
	var wine89val = E8val;
	var losse89n = E9n;
} else {
	var wine89n = E9n;
	var wine89val = E9val;
	var losse89n = E8n;
}
} else {
	var r17 = prob(E9val, E8val)
	if (rn17 > r17) {
	var wine89n = E8n;
	var wine89val = E8val;
	var losse89n = E9n;
} else {
	var wine89n = E9n;
	var wine89val = E9val;
	var losse89n = E8n;
}
}
let rn18 = [Math.random()];
if (E5val < E12val) {
	var r18 = prob(E5val, E12val)
	if (r18 > rn18) {
	var wine512n = E5n;
	var wine512val = E5val;
	var losse512n = E12n;
} else {
	var wine512n = E12n;
	var wine512val = E12val;
	var losse512n = E5n;
}
} else {
	var r18 = prob(E12val, E5val)
	if (rn18 > r18) {
	var wine512n = E5n;
	var wine512val = E5val;
	var losse512n = E12n;
} else {
	var wine512n = E12n;
	var wine512val = E12val;
	var losse512n = E5n;
}
}
let rn19 = [Math.random()];
if (E4val < E13val) {
	var r19 = prob(E4val, E1val)
	if (r19 > rn19) {
	var wine413n = E4n;
	var wine413val = E4val;
	var losse413n = E13n;
} else {
	var wine413n = E13n;
	var wine413val = E13val;
	var losse413n = E4n;
}
} else {
	var r19 = prob(E13val, E4val)
	if (rn19 > r19) {
	var wine413n = E4n;
	var wine413val = E4val;
	var losse413n = E13n;
} else {
	var wine413n = E13n;
	var wine413val = E13val;
	var losse413n = E4n;
}
}
let rn20 = [Math.random()];
if (E6val < E11val) {
	var r20 = prob(E6val, E11val)
	if (r20 > rn20) {
	var wine611n = E6n;
	var wine611val = E6val;
	var losse611n = E11n;
} else {
	var wine611n = E11n;
	var wine611val = E11val;
	var losse611n = E6n;
}
} else {
	var r20 = prob(E11val, E6val)
	if (rn20 > r20) {
	var wine611n = E6n;
	var wine611val = E6val;
	var losse611n = E11n;
} else {
	var wine611n = Elln;
	var wine611val = E11val;
	var losse611n = E6n;
}
}
let rn21 = [Math.random()];
if (E3val < E14val) {
	var r21 = prob(E3val, E14val)
	if (r21 > rn21) {
	var wine314n = E3n;
	var wine314val = E3val;
	var losse314n = E14n;
} else {
	var wine314n = E14n;
	var wine314val = E14val;
	var losse314n = E3n;
}
} else {
	var r21 = prob(E14val, E3val)
	if (rn21 > r21) {
	var wine314n = E3n;
	var wine314val = E3val;
	var losse314n = E14n;
} else {
	var wine314n = E14n;
	var wine314val = E14val;
	var losse314n = E3n;
}
}
let rn22 = [Math.random()];
if (E7val < E10val) {
	var r22 = prob(E7val, E10val)
	if (r22 > rn22) {
	var wine710n = E7n;
	var wine710val = E7val;
	var losse710n = E10n;
} else {
	var wine710n = E10n;
	var wine710val = E10val;
	var losse710n = E7n;
}
} else {
	var r22 = prob(E10val, E7val)
	if (rn22 > r22) {
	var wine710n = E7n;
	var wine710val = E7val;
	var losse710n = E10n;
} else {
	var wine710n = E10n;
	var wine710val = E10val;
	var losse710n = E7n;
}
}
let rn23 = [Math.random()];
if (E2val < E15val) {
	var r23 = prob(E2val, E15val)
	if (r23 > rn23) {
	var wine215n = E2n;
	var wine215val = E2val;
	var losse215n = E15n;
} else {
	var wine215n = E15n;
	var wine215val = E15val;
	var losse215n = E2n;
}
} else {
	var r23 = prob(E15val, E2val)
	if (rn23 > r23) {
	var wine215n = E2n;
	var wine215val = E2val;
	var losse215n = E15n;
} else {
	var wine215n = E15n;
	var wine215val = E15val;
	var losse215n = E2n;
}
}

let rn24 = [Math.random()];
if (wine116val < wine89val) {
	var r24 = prob(wine116val, wine89val)
	if (r24 > rn24) {
	var wine18n = wine116n;
	var wine18val = wine116val;
	var losse18n = wine89n;
} else {
	var wine18n = wine89n;
	var wine18val = wine89val;
	var losse18n = wine116n;
}
} else {
	var r24 = prob(wine89val, wine116val)
	if (rn24 > r24) {
	var wine18n = wine116n;
	var wine18val = wine116val;
	var losse18n = wine89n;
} else {
	var wine18n = wine89n;
	var wine18val = wine89val;
	var losse18n = wine116n;
}
}
let rn25 = [Math.random()];
if (wine512val < wine413val) {
	var r25 = prob(wine512val, wine413val)
	if (r25 > rn25) {
	var wine45n = wine512n;
	var wine45val = wine512val;
	var losse45n = wine413n;
} else {
	var wine45n = wine413n;
	var wine45val = wine413val;
	var losse45n = wine512n;
}
} else {
	var r25 = prob(wine413val, wine512val)
	if (rn25 > r25) {
	var wine45n = wine512n;
	var wine45val = wine512val;
	var losse45n = wine413n;
} else {
	var wine45n = wine413n;
	var wine45val = wine413val;
	var losse45n = wine512n;
}
}
let rn26 = [Math.random()];
if (wine611val < wine314val) {
	var r26 = prob(wine611val, wine314val)
	if (r26 > rn26) {
	var wine36n = wine611n;
	var wine36val = wine611val;
	var losse36n = wine314n;
} else {
	var wine36n = wine314n;
	var wine36val = wine314val;
	var losse36n = wine611n;
}
} else {
	var r26 = prob(wine314val, wine611val)
	if (rn26 > r26) {
	var wine36n = wine611n;
	var wine36val = wine611val;
	var losse36n = wine314n;
} else {
	var wine36n = wine314n;
	var wine36val = wine314val;
	var losse36n = wine611n;
}
}
let rn27 = [Math.random()];
if (wine710val < wine215val) {
	var r27 = prob(wine710val, wine215val)
	if (r27 > rn27) {
	var wine27n = wine710n;
	var wine27val = wine710val;
	var losse27n = wine215n;
} else {
	var wine27n = wine215n;
	var wine27val = wine215val;
	var losse27n = wine710n;
}
} else {
	var r27 = prob(wine215val, wine710val)
	if (rn27 > r27) {
	var wine27n = wine710n;
	var wine27val = wine710val;
	var losse27n = wine215n;
} else {
	var wine27n = wine215n;
	var wine27val = wine215val;
	var losse27n = wine710n;
}
}

let rn28 = [Math.random()];
if (wine18val < wine45val) {
	var r28 = prob(wine18val, wine45val)
	if (r28 > rn28) {
	var wine14n = wine18n;
	var wine14val = wine18val;
	var losse14n = wine45n;
} else {
	var wine14n = wine45n;
	var wine14val = wine45val;
	var losse14n = wine18n;
}
} else {
	var r28 = prob(wine45val, wine18val)
	if (rn28 > r28) {
	var wine14n = wine18n;
	var wine14val = wine18val;
	var losse14n = wine45n;
} else {
	var wine14n = wine45n;
	var wine14val = wine45val;
	var losse14n = wine18n;
}
}
let rn29 = [Math.random()];
if (wine36val < wine27val) {
	var r29 = prob(wine36val, wine27val)
	if (r29 > rn29) {
	var wine23n = wine36n;
	var wine23val = wine36val;
	var losse23n = wine27n;
} else {
	var wine23n = wine27n;
	var wine23val = wine27val;
	var losse23n = wine36n;
}
} else {
	var r29 = prob(wine27val, wine36val)
	if (rn29 > r29) {
	var wine23n = wine36n;
	var wine23val = wine36val;
	var losse23n = wine27n;
} else {
	var wine23n = wine27n;
	var wine23val = wine27val;
	var losse23n = wine36n;
}
}
let rn30 = [Math.random()];
if (wine14val < wine23val) {
	var r30 = prob(wine14val, wine23val)
	if (r30 > rn30) {
	var wine12n = wine14n;
	var wine12val = wine14val;
	var losse12n = wine23n;
} else {
	var wine12n = wine23n;
	var wine12val = wine23val;
	var losse12n = wine14n;
}
} else {
	var r30 = prob(wine23val, wine14val)
	if (rn30 > r30) {
	var wine12n = wine14n;
	var wine12val = wine14val;
	var losse12n = wine23n;
} else {
	var wine12n = wine23n;
	var wine12val = wine23val;
	var losse12n = wine14n;
}
}

let rn0b = [Math.random()];
if (S10aval < S10bval) {
	var r0b = prob(S10aval, S10bval)
	if (r0b > rn0b) {
	var winsplayinn = S10an;
	var winsplayinval = S10aval;
	var losssplayinn = S10bn;
} else {
	var winsplayinn = S10bn;
	var winsplayinval = S10bval;
	var losssplayinn = S10an;
}
} else {
	var r0b = prob(S10bval, S10aval)
	if (rn0b > r0b) {
	var winsplayinn = S10an;
	var winsplayinval = S10aval;
	var losssplayinn = S10bn;
} else {
	var winsplayinn = S10bn;
	var winsplayinval = S10bval;
	var losssplayinn = S10an;
}
}
let rn32 = [Math.random()];
if (S1val < S16val) {
	if (r32 > rn32) {
	var wins116n = S1n;
	var wins116val = S1val;
	var losss116n = S16n;
} else {
	var wins116n = S16n;
	var wins116val = S16val;
	var losss116n = S1n;
}
} else {
	var r32 = prob(S16val, S1val)
	if (rn32 > r32) {
	var wins116n = S1n;
	var wins116val = S1val;
	var losss116n = S16n;
} else {
	var wins116n = S16n;
	var wins116val = S16val;
	var losss116n = S1n;
}
}
let rn33 = [Math.random()];
if (S8val < S9val) {
	var r33 = prob(S8val, S9val)
	if (r33 > rn33) {
	var wins89n = S8n;
	var wins89val = S8val;
	var losss89n = S9n;
} else {
	var wins89n = S9n;
	var wins89val = S9val;
	var losss89n = S8n;
}
} else {
	var r33 = prob(S9val, S8val)
	if (rn33 > r33) {
	var wins89n = S8n;
	var wins89val = S8val;
	var losss89n = S9n;
} else {
	var wins89n = S9n;
	var wins89val = S9val;
	var losss89n = S8n;
}
}
let rn34 = [Math.random()];
if (S5val < S12val) {
	var r34 = prob(S5val, S12val)
	if (r34 > rn34) {
	var wins512n = S5n;
	var wins512val = S5val;
	var losss512n = S12n;
} else {
	var wins512n = S12n;
	var wins512val = S12val;
	var losss512n = S5n;
}
} else {
	var r34 = prob(S12val, S5val)
	if (rn34 > r34) {
	var wins512n = S5n;
	var wins512val = S5val;
	var losss512n = S12n;
} else {
	var wins512n = S12n;
	var wins512val = S12val;
	var losss512n = S5n;
}
}
let rn35 = [Math.random()];
if (S4val < S13val) {
	var r35 = prob(S4val, S1val)
	if (r35 > rn35) {
	var wins413n = S4n;
	var wins413val = S4val;
	var losss413n = S13n;
} else {
	var wins413n = S13n;
	var wins413val = S13val;
	var losss413n = S4n;
}
} else {
	var r35 = prob(S13val, S4val)
	if (rn35 > r35) {
	var wins413n = S4n;
	var wins413val = S4val;
	var losss413n = S13n;
} else {
	var wins413n = S13n;
	var wins413val = S13val;
	var losss413n = S4n;
}
}
let rn36 = [Math.random()];
if (S6val < S11val) {
	var r36 = prob(S6val, S11val)
	if (r36 > rn36) {
	var wins611n = S6n;
	var wins611val = S6val;
	var losss611n = S11n;
} else {
	var wins611n = S11n;
	var wins611val = S11val;
	var losss611n = S6n;
}
} else {
	var r36 = prob(S11val, S6val)
	if (rn36 > r36) {
	var wins611n = S6n;
	var wins611val = S6val;
	var losss611n = S11n;
} else {
	var wins611n = S11n;
	var wins611val = S11val;
	var losss611n = S6n;
}
}
let rn37 = [Math.random()];
if (S3val < S14val) {
	var r37 = prob(S3val, S14val)
	if (r37 > rn37) {
	var wins314n = S3n;
	var wins314val = S3val;
	var losss314n = S14n;
} else {
	var wins314n = S14n;
	var wins314val = S14val;
	var losss314n = S3n;
}
} else {
	var r37 = prob(S14val, S3val)
	if (rn37 > r37) {
	var wins314n = S3n;
	var wins314val = S3val;
	var losss314n = S14n;
} else {
	var wins314n = S14n;
	var wins314val = S14val;
	var losss314n = S3n;
}
}
let rn38 = [Math.random()];
if (S7val < winsplayinval) {
	var r38 = prob(S7val, winsplayinval)
	if (r38 > rn38) {
	var wins710n = S7n;
	var wins710val = S7val;
	var losss710n = winsplayinn;
} else {
	var wins710n = winsplayinn;
	var wins710val = winsplayinval;
	var losss710n = S7n;
}
} else {
	var r38 = prob(winsplayinval, S7val)
	if (rn38 > r38) {
	var wins710n = S7n;
	var wins710val = S7val;
	var losss710n = winsplayinn;
} else {
	var wins710n = winsplayinn;
	var wins710val = winsplayinval;
	var losss710n = S7n;
}
}
let rn39 = [Math.random()];
if (S2val < S15val) {
	var r39 = prob(S2val, S15val)
	if (r39 > rn39) {
	var wins215n = S2n;
	var wins215val = S2val;
	var losss215n = S15n;
} else {
	var wins215n = S15n;
	var wins215val = S15val;
	var losss215n = S2n;
}
} else {
	var r39 = prob(S15val, S2val)
	if (rn39 > r39) {
	var wins215n = S2n;
	var wins215val = S2val;
	var losss215n = S15n;
} else {
	var wins215n = S15n;
	var wins215val = S15val;
	var losss215n = S2n;
}
}

let rn40 = [Math.random()];
if (wins116val < wins89val) {
	var r40 = prob(wins116val, wins89val)
	if (r40 > rn40) {
	var wins18n = wins116n;
	var wins18val = wins116val;
	var losss18n = wins89n;
} else {
	var wins18n = wins89n;
	var wins18val = wins89val;
	var losss18n = wins116n;
}
} else {
	var r40 = prob(wins89val, wins116val)
	if (rn40 > r40) {
	var wins18n = wins116n;
	var wins18val = wins116val;
	var losss18n = wins89n;
} else {
	var wins18n = wins89n;
	var wins18val = wins89val;
	var losss18n = wins116n;
}
}
let rn41 = [Math.random()];
if (wins512val < wins413val) {
	var r41 = prob(wins512val, wins413val)
	if (r41 > rn41) {
	var wins45n = wins512n;
	var wins45val = wins512val;
	var losss45n = wins413n;
} else {
	var wins45n = wins413n;
	var wins45val = wins413val;
	var losss45n = wins512n;
}
} else {
	var r41 = prob(wins413val, wins512val)
	if (rn41 > r41) {
	var wins45n = wins512n;
	var wins45val = wins512val;
	var losss45n = wins413n;
} else {
	var wins45n = wins413n;
	var wins45val = wins413val;
	var losss45n = wins512n;
}
}
let rn42 = [Math.random()];
if (wins611val < wins314val) {
	var r42 = prob(wins611val, wins314val)
	if (r42 > rn42) {
	var wins36n = wins611n;
	var wins36val = wins611val;
	var losss36n = wins314n;
} else {
	var wins36n = wins314n;
	var wins36val = wins314val;
	var losss36n = wins611n;
}
} else {
	var r42 = prob(wins314val, wins611val)
	if (rn42 > r42) {
	var wins36n = wins611n;
	var wins36val = wins611val;
	var losss36n = wins314n;
} else {
	var wins36n = wins314n;
	var wins36val = wins314val;
	var losss36n = wins611n;
}
}
let rn43 = [Math.random()];
if (wins710val < wins215val) {
	var r43 = prob(wins710val, wins215val)
	if (r43 > rn43) {
	var wins27n = wins710n;
	var wins27val = wins710val;
	var losss27n = wins215n;
} else {
	var wins27n = wins215n;
	var wins27val = wins215val;
	var losss27n = wins710n;
}
} else {
	var r43 = prob(wins215val, wins710val)
	if (rn43 > r43) {
	var wins27n = wins710n;
	var wins27val = wins710val;
	var losss27n = wins215n;
} else {
	var wins27n = wins215n;
	var wins27val = wins215val;
	var losss27n = wins710n;
}
}

let rn44 = [Math.random()];
if (wins18val < wins45val) {
	var r44 = prob(wins18val, wins45val)
	if (r44 > rn44) {
	var wins14n = wins18n;
	var wins14val = wins18val;
	var losss14n = wins45n;
} else {
	var wins14n = wins45n;
	var wins14val = wins45val;
	var losss14n = wins18n;
}
} else {
	var r44 = prob(wins45val, wins18val)
	if (rn44 > r44) {
	var wins14n = wins18n;
	var wins14val = wins18val;
	var losss14n = wins45n;
} else {
	var wins14n = wins45n;
	var wins14val = wins45val;
	var losss14n = wins18n;
}
}
let rn45 = [Math.random()];
if (wins36val < wins27val) {
	var r45 = prob(wins36val, wins27val)
	if (r45 > rn45) {
	var wins23n = wins36n;
	var wins23val = wins36val;
	var losss23n = wins27n;
} else {
	var wins23n = wins27n;
	var wins23val = wins27val;
	var losss23n = wins36n;
}
} else {
	var r45 = prob(wins27val, wins36val)
	if (rn45 > r45) {
	var wins23n = wins36n;
	var wins23val = wins36val;
	var losss23n = wins27n;
} else {
	var wins23n = wins27n;
	var wins23val = wins27val;
	var losss23n = wins36n;
}
}
let rn46 = [Math.random()];
if (wins14val < wins23val) {
	var r46 = prob(wins14val, wins23val)
	if (r46 > rn46) {
	var wins12n = wins14n;
	var wins12val = wins14val;
	var losss12n = wins23n;
} else {
	var wins12n = wins23n;
	var wins12val = wins23val;
	var losss12n = wins14n;
}
} else {
	var r46 = prob(wins23val, wins14val)
	if (rn46 > r46) {
	var wins12n = wins14n;
	var wins12val = wins14val;
	var losss12n = wins23n;
} else {
	var wins12n = wins23n;
	var wins12val = wins23val;
	var losss12n = wins14n;
}
}

let rn0c = [Math.random()];
if (MW16aval < MW16bval) {
	var r0c = prob(MW16aval, MW16bval)
	if (r0c > rn0c) {
	var winmwplayinn = MW16an;
	var winmwplayinval = MW16aval;
	var lossmwplayinn = MW16bn;
} else {
	var winmwplayinn = MW16bn;
	var winmwplayinval = MW16bval;
	var lossmwplayinn = MW16an;
}
} else {
	var r0c = prob(MW16bval, MW16aval)
	if (rn0c > r0c) {
	var winmwplayinn = MW16an;
	var winmwplayinval = MW16aval;
	var lossmwplayinn = MW16bn;
} else {
	var winmwplayinn = MW16bn;
	var winmwplayinval = MW16bval;
	var lossmwplayinn = MW16an;
}
}
let rn0d = [Math.random()];
if (MW10aval < MW10bval) {
	var r0d = prob(MW10aval, MW10bval)
	if (r0d > rn0d) {
	var winmwplayin2n = MW10an;
	var winmwplayin2val = MW10aval;
	var lossmwplayin2n = MW10bn;
} else {
	var winmwplayin2n = MW10bn;
	var winmwplayin2val = MW10bval;
	var lossmwplayin2n = MW10an;
}
} else {
	var r0d = prob(MW10bval, MW10aval)
	if (rn0d > r0d) {
	var winmwplayin2n = MW10an;
	var winmwplayin2val = MW10aval;
	var lossmwplayin2n = MW10bn;
} else {
	var winmwplayin2n = MW10bn;
	var winmwplayin2val = MW10bval;
	var lossmwplayin2n = MW10an;
}
}

let rn47 = [Math.random()];
if (MW1val < winmwplayinval) {
	var r47 = prob(MW1val, winmwplayinval)
	if (r47 > rn47) {
	var winmw116n = MW1n;
	var winmw116val = MW1val;
	var lossmw116n = winmwplayinn;
} else {
	var winmw116n = winmwplayinn;
	var winmw116val = winmwplayinval;
	var lossmw116n = MW1n;
}
} else {
	var r47 = prob(winmwplayinval, MW1val)
	if (rn47 > r47) {
	var winmw116n = MW1n;
	var winmw116val = MW1val;
	var lossmw116n = winmwplayinn;
} else {
	var winmw116n = winmwplayinn;
	var winmw116val = winmwplayinval;
	var lossmw116n = MW1n;
}
}
let rn48 = [Math.random()];
if (MW8val < MW9val) {
	var r48 = prob(MW8val, MW9val)
	if (r48 > rn48) {
	var winmw89n = MW8n;
	var winmw89val = MW8val;
	var lossmw89n = MW9n;
} else {
	var winmw89n = MW9n;
	var winmw89val = MW9val;
	var lossmw89n = MW8n;
}
} else {
	var r48 = prob(MW9val, MW8val)
	if (rn48 > r48) {
	var winmw89n = MW8n;
	var winmw89val = MW8val;
	var lossmw89n = MW9n;
} else {
	var winmw89n = MW9n;
	var winmw89val = MW9val;
	var lossmw89n = MW8n;
}
}
let rn49 = [Math.random()];
if (MW5val < MW12val) {
	var r49 = prob(MW5val, MW12val)
	if (r49 > rn49) {
	var winmw512n = MW5n;
	var winmw512val = MW5val;
	var lossmw512n = MW12n;
} else {
	var winmw512n = MW12n;
	var winmw512val = MW12val;
	var lossmw512n = MW5n;
}
} else {
	var r49 = prob(MW12val, MW5val)
	if (rn49 > r49) {
	var winmw512n = MW5n;
	var winmw512val = MW5val;
	var lossmw512n = MW12n;
} else {
	var winmw512n = MW12n;
	var winmw512val = MW12val;
	var lossmw512n = MW5n;
}
}
let rn50 = [Math.random()];
if (MW4val < MW13val) {
	var r50 = prob(MW4val, MW1val)
	if (r50 > rn50) {
	var winmw413n = MW4n;
	var winmw413val = MW4val;
	var lossmw413n = MW13n;
} else {
	var winmw413n = MW13n;
	var winmw413val = MW13val;
	var lossmw413n = MW4n;
}
} else {
	var r50 = prob(MW13val, MW4val)
	if (rn50 > r50) {
	var winmw413n = MW4n;
	var winmw413val = MW4val;
	var lossmw413n = MW13n;
} else {
	var winmw413n = MW13n;
	var winmw413val = MW13val;
	var lossmw413n = MW4n;
}
}
let rn51 = [Math.random()];
if (MW6val < winmwplayinval) {
	var r51 = prob(MW6val, winmwplayinval)
	if (r51 > rn51) {
	var winmw611n = MW6n;
	var winmw611val = MW6val;
	var lossmw611n = winmwplayinn;
} else {
	var winmw611n = winmwplayinn;
	var winmw611val = winmwplayinval;
	var lossmw611n = MW6n;
}
} else {
	var r51 = prob(winmwplayinval, MW6val)
	if (rn51 > r51) {
	var winmw611n = MW6n;
	var winmw611val = MW6val;
	var lossmw611n = winmwplayinn;
} else {
	var winmw611n = winmwplayinn;
	var winmw611val = winmwplayinval;
	var lossmw611n = MW6n;
}
}
let rn52 = [Math.random()];
if (MW3val < MW14val) {
	var r52 = prob(MW3val, MW14val)
	if (r52 > rn52) {
	var winmw314n = MW3n;
	var winmw314val = MW3val;
	var lossmw314n = MW14n;
} else {
	var winmw314n = MW14n;
	var winmw314val = MW14val;
	var lossmw314n = MW3n;
}
} else {
	var r52 = prob(MW14val, MW3val)
	if (rn52 > r52) {
	var winmw314n = MW3n;
	var winmw314val = MW3val;
	var lossmw314n = MW14n;
} else {
	var winmw314n = MW14n;
	var winmw314val = MW14val;
	var lossmw314n = MW3n;
}
}
let rn53 = [Math.random()];
if (MW7val < winmwplayin2val) {
	var r53 = prob(MW7val, winmwplayin2val)
	if (r53 > rn53) {
	var winmw710n = MW7n;
	var winmw710val = MW7val;
	var lossmw710n = winmwplayin2n;
} else {
	var winmw710n = winmwplayin2n;
	var winmw710val = winmwplayin2val;
	var lossmw710n = MW7n;
}
} else {
	var r53 = prob(winmwplayin2val, MW7val)
	if (rn53 > r53) {
	var winmw710n = MW7n;
	var winmw710val = MW7val;
	var lossmw710n = winmwplayin2n;
} else {
	var winmw710n = winmwplayin2n;
	var winmw710val = winmwplayin2val;
	var lossmw710n = MW7n;
}
}
let rn54 = [Math.random()];
if (MW2val < MW15val) {
	var r54 = prob(MW2val, MW15val)
	if (r54 > rn54) {
	var winmw215n = MW2n;
	var winmw215val = MW2val;
	var lossmw215n = MW15n;
} else {
	var winmw215n = MW15n;
	var winmw215val = MW15val;
	var lossmw215n = MW2n;
}
} else {
	var r54 = prob(MW15val, MW2val)
	if (rn54 > r54) {
	var winmw215n = MW2n;
	var winmw215val = MW2val;
	var lossmw215n = MW15n;
} else {
	var winmw215n = MW15n;
	var winmw215val = MW15val;
	var lossmw215n = MW2n;
}
}

let rn55 = [Math.random()];
if (winmw116val < winmw89val) {
	var r55 = prob(winmw116val, winmw89val)
	if (r55 > rn55) {
	var winmw18n = winmw116n;
	var winmw18val = winmw116val;
	var lossmw18n = winmw89n;
} else {
	var winmw18n = winmw89n;
	var winmw18val = winmw89val;
	var lossmw18n = winmw116n;
}
} else {
	var r55 = prob(winmw89val, winmw116val)
	if (rn55 > r55) {
	var winmw18n = winmw116n;
	var winmw18val = winmw116val;
	var lossmw18n = winmw89n;
} else {
	var winmw18n = winmw89n;
	var winmw18val = winmw89val;
	var lossmw18n = winmw116n;
}
}
let rn56 = [Math.random()];
if (winmw512val < winmw413val) {
	var r56 = prob(winmw512val, winmw413val)
	if (r56 > rn56) {
	var winmw45n = winmw512n;
	var winmw45val = winmw512val;
	var lossmw45n = winmw413n;
} else {
	var winmw45n = winmw413n;
	var winmw45val = winmw413val;
	var lossmw45n = winmw512n;
}
} else {
	var r56 = prob(winmw413val, winmw512val)
	if (rn56 > r56) {
	var winmw45n = winmw512n;
	var winmw45val = winmw512val;
	var lossmw45n = winmw413n;
} else {
	var winmw45n = winmw413n;
	var winmw45val = winmw413val;
	var lossmw45n = winmw512n;
}
}
let rn57 = [Math.random()];
if (winmw611val < winmw314val) {
	var r57 = prob(winmw611val, winmw314val)
	if (r57 > rn57) {
	var winmw36n = winmw611n;
	var winmw36val = winmw611val;
	var lossmw36n = winmw314n;
} else {
	var winmw36n = winmw314n;
	var winmw36val = winmw314val;
	var lossmw36n = winmw611n;
}
} else {
	var r57 = prob(winmw314val, winmw611val)
	if (rn57 > r57) {
	var winmw36n = winmw611n;
	var winmw36val = winmw611val;
	var lossmw36n = winmw314n;
} else {
	var winmw36n = winmw314n;
	var winmw36val = winmw314val;
	var lossmw36n = winmw611n;
}
}
let rn58 = [Math.random()];
if (winmw710val < winmw215val) {
	var r58 = prob(winmw710val, winmw215val)
	if (r58 > rn58) {
	var winmw27n = winmw710n;
	var winmw27val = winmw710val;
	var lossmw27n = winmw215n;
} else {
	var winmw27n = winmw215n;
	var winmw27val = winmw215val;
	var lossmw27n = winmw710n;
}
} else {
	var r58 = prob(winmw215val, winmw710val)
	if (rn58 > r58) {
	var winmw27n = winmw710n;
	var winmw27val = winmw710val;
	var lossmw27n = winmw215n;
} else {
	var winmw27n = winmw215n;
	var winmw27val = winmw215val;
	var lossmw27n = winmw710n;
}
}
let rn59 = [Math.random()];
if (winmw18val < winmw45val) {
	var r59 = prob(winmw18val, winmw45val)
	if (r59 > rn59) {
	var winmw14n = winmw18n;
	var winmw14val = winmw18val;
	var lossmw14n = winmw45n;
} else {
	var winmw14n = winmw45n;
	var winmw14val = winmw45val;
	var lossmw14n = winmw18n;
}
} else {
	var r59 = prob(winmw45val, winmw18val)
	if (rn59 > r59) {
	var winmw14n = winmw18n;
	var winmw14val = winmw18val;
	var lossmw14n = winmw45n;
} else {
	var winmw14n = winmw45n;
	var winmw14val = winmw45val;
	var lossmw14n = winmw18n;
}
}
let rn60 = [Math.random()];
if (winmw36val < winmw27val) {
	var r60 = prob(winmw36val, winmw27val)
	if (r60 > rn60) {
	var winmw23n = winmw36n;
	var winmw23val = winmw36val;
	var lossmw23n = winmw27n;
} else {
	var winmw23n = winmw27n;
	var winmw23val = winmw27val;
	var lossmw23n = winmw36n;
}
} else {
	var r60 = prob(winmw27val, winmw36val)
	if (rn60 > r60) {
	var winmw23n = winmw36n;
	var winmw23val = winmw36val;
	var lossmw23n = winmw27n;
} else {
	var winmw23n = winmw27n;
	var winmw23val = winmw27val;
	var lossmw23n = winmw36n;
}
}
let rn61 = [Math.random()];
if (winmw14val < winmw23val) {
	var r60 = prob(winmw14val, winmw23val)
	if (r61 > rn61) {
	var winmw12n = winmw14n;
	var winmw12val = winmw14val;
	var lossmw12n = winmw23n;
} else {
	var winmw12n = winmw23n;
	var winmw12val = winmw23val;
	var lossmw12n = winmw14n;
}
} else {
	var r61 = prob(winmw23val, winmw14val)
	if (rn61 > r61) {
	var winmw12n = winmw14n;
	var winmw12val = winmw14val;
	var lossmw12n = winmw23n;
} else {
	var winmw12n = winmw23n;
	var winmw12val = winmw23val;
	var lossmw12n = winmw14n;
}
}


let rn31 = [Math.random()];
if (winw12val < wine12val) {
	var r31 = prob(winw12val, wine12val)
	if (r31 > rn31) {
	var winleftn = winw12n;
	var winleftval = winw12val;
	var lossleftn = wine12n;
} else {
	var winleftn = wine12n;
	var winleftval = wine12val;
	var lossleftn = winw12n;
}
} else {
	var r31 = prob(wine12val, winw12val)
	if (rn31 > r31) {
	var winleftn = wine12n;
	var winleftval = wine12val;
	var lossleftn = winw12n;
} else {
	var winleftn = winw12n;
	var winleftval = winw12val;
	var lossleftn = wine12n;
}
}

let rn62 = [Math.random()];
if (wins12val < winmw12val) {
	var r62 = prob(wins12val, winmw12val)
	if (r62 > rn62) {
	var winrightn = wins12n;
	var winrightval = wins12val;
	var lossrightn = winmw12n;
} else {
	var winrightn = winmw12n;
	var winrightval = winmw12val;
	var lossrightn = wins12n;
}
} else {
	var r62 = prob(winmw12val, wins12val)
	if (rn62 > r62) {
	var winrightn = winmw12n;
	var winrightval = winmw12val;
	var lossrightn = wins12n;
} else {
	var winrightn = wins12n;
	var winrightval = wins12val;
	var lossrightn = winmw12n;
}
}
let rn63 = [Math.random()];
if (winleftval < winrightval) {
	var r63 = prob(winleftval, winrightval)
	if (r63 > rn63) {
	var winchampn = winleftn;
	var winchampval = winleftval;
	var losschampn = winrightn;
} else {
	var winchampn = winrightn;
	var winchampval = winrightval;
	var losschampn = winleftn;
}
} else {
	var r63 = prob(winrightval, winleftval)
	if (rn63 > r63) {
	var winchampn = winrightn;
	var winchampval = winrightval;
	var losschampn = winleftn;
} else {
	var winchampn = winleftn;
	var winchampval = winleftval;
	var losschampn = winrightn;
}
}


document.getElementById("demo").innerHTML = 
"<b> PLAY-INS </b>" + "</br>" +
wineplayinn + " beats " + losseplayinn + "</br>" +
winsplayinn + " beats " + losssplayinn + "</br>" +
winmwplayinn + " beats " + lossmwplayinn + "</br>" + 
winmwplayin2n + " beats " + lossmwplayin2n + "</br>" +
"<b> ROUND ONE </b>" + "</br>" +
winw116n + " beats " + lossw116n + "</br>" +
winw89n + " beats " + lossw89n + "</br>" +
winw512n + " beats " + lossw512n + "</br>" +
winw413n + " beats " + lossw413n + "</br>" +
winw611n + " beats " + lossw611n + "</br>" +
winw314n + " beats " + lossw314n + "</br>" +
winw710n + " beats " + lossw710n + "</br>" +
winw215n + " beats " + lossw215n + "</br>" + "</br>"+
wine116n + " beats " + losse116n + "</br>" +
wine89n + " beats " + losse89n + "</br>" +
wine512n + " beats " + losse512n + "</br>" +
wine413n + " beats " + losse413n + "</br>" +
wine611n + " beats " + losse611n + "</br>" +
wine314n + " beats " + losse314n + "</br>" +
wine710n + " beats " + losse710n + "</br>" +
wine215n + " beats " + losse215n + "</br>" + "</br>" +
wins116n + " beats " + losss116n + "</br>" +
wins89n + " beats " + losss89n + "</br>" +
wins512n + " beats " + losss512n + "</br>" +
wins413n + " beats " + losss413n + "</br>" +
wins611n + " beats " + losss611n + "</br>" +
wins314n + " beats " + losss314n + "</br>" +
wins710n + " beats " + losss710n + "</br>" +
wins215n + " beats " + losss215n + "</br>" + "</br>" +
winmw116n + " beats " + lossmw116n + "</br>" +
winmw89n + " beats " + lossmw89n + "</br>" +
winmw512n + " beats " + lossmw512n + "</br>" +
winmw413n + " beats " + lossmw413n + "</br>" +
winmw611n + " beats " + lossmw611n + "</br>" +
winmw314n + " beats " + lossmw314n + "</br>" +
winmw710n + " beats " + lossmw710n + "</br>" +
winmw215n + " beats " + lossmw215n + "</br>" + "</br>" +
"<b> ROUND TWO </b>" + "</br>" +
winw18n + " beats " + lossw18n + "</br>" +
winw45n + " beats " + lossw45n + "</br>" +
winw36n + " beats " + lossw36n + "</br>" +
winw27n + " beats " + lossw27n + "</br>" + "</br>" +
wine18n + " beats " + losse18n + "</br>" +
wine45n + " beats " + losse45n + "</br>" +
wine36n + " beats " + losse36n + "</br>" +
wine27n + " beats " + losse27n + "</br>" + "</br>" +
wins18n + " beats " + losss18n + "</br>" +
wins45n + " beats " + losss45n + "</br>" +
wins36n + " beats " + losss36n + "</br>" +
wins27n + " beats " + losss27n + "</br>" + "</br>" +
winmw18n + " beats " + lossmw18n + "</br>" +
winmw45n + " beats " + lossmw45n + "</br>" +
winmw36n + " beats " + lossmw36n + "</br>" +
winmw27n + " beats " + lossmw27n + "</br>" + "</br>" +
"<b> SWEET SIXTEEN </b>" + "</br>" +
winw14n + " beats " + lossw14n + "</br>" +
winw23n + " beats " + lossw23n + "</br>" + "</br>" +
wine14n + " beats " + losse14n + "</br>" +
wine23n + " beats " + losse23n + "</br>" + "</br>" +
wins14n + " beats " + losss14n + "</br>" +
wins23n + " beats " + losss23n + "</br>" + "</br>" +
winmw14n + " beats " + lossmw14n + "</br>" +
winmw23n + " beats " + lossmw23n + "</br>" + "</br>" +
"<b> ELITE EIGHT </b>" + "</br>" +
winw12n + " beats " + lossw12n + "</br>" + "</br>" +
wine12n + " beats " + losse12n + "</br>" + "</br>" +
wins12n + " beats " + losss12n + "</br>" + "</br>" +
winmw12n + " beats " + lossmw12n + "</br>" + "</br>" +
"<b> FINAL FOUR </b>" + "</br>" +
winleftn + " beats " + lossleftn + "</br>" +
winrightn + " beats " + lossrightn + "</br>" + "</br>" +
"<b> CHAMPIONSHIP GAME </b>" + "</br>" +
winchampn + " beats " + losschampn + "</br>" +
"<b> YOUR 2021 CHAMPION IS </b>" + winchampn + "<b> !!!! </b>";
}
</script>
</body>
</html>
