<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8" />
<title>Quadratic Bezier Curve</title>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
<style>
	* {
		margin: 0;
		padding: 0;
	}

	html, body {
		width: 100%;
		height: 100%;
		overflow: hidden;
	}

	svg {
		width: 100%;
		height: 100%;
		outline: 1px dotted blue;
	}
</style>
</head>
	
<body>
	<p id="status"></p>
	<svg id="mysvg"></svg>

	<script>
		$(document).ready(function(){
			var mx, my, mdptx, mx_rel_5, mx_10_rel, random, docw, doch, svgw, svgh;
			var svg = $("#mysvg");

			svg.on("mousemove", function(e){
				//mouse_coordinates relative to document
				mx = e.clientX;
				my = e.clientY;

				mx_5 = mx/5;
				mx_10 = mx/10;

				//coordinate starts from center of document
				mx_rel = mx - mdptx;

				mx_rel_5 = mx_rel/5;
				mx_rel_10 = mx_rel/10;

				createPath();
			});

			setInterval(function(){
				random = {
					a: Math.floor(Math.random()*150),
					b: Math.floor(Math.random()*150),
					c: Math.floor(Math.random()*150),
					d: Math.floor(Math.random()*150),
					e: Math.floor(Math.random()*150),
					f: Math.floor(Math.random()*150),
					g: Math.floor(Math.random()*150),
					h: Math.floor(Math.random()*150),
					i: Math.floor(Math.random()*150),
					j: Math.floor(Math.random()*150),
					k: Math.floor(Math.random()*150),
					l: Math.floor(Math.random()*150),
					m: Math.floor(Math.random()*150),
					n: Math.floor(Math.random()*150),
					o: Math.floor(Math.random()*150),
					p: Math.floor(Math.random()*150),
					q: Math.floor(Math.random()*150),
					r: Math.floor(Math.random()*150),
					s: Math.floor(Math.random()*150),
					t: Math.floor(Math.random()*150),
					u: Math.floor(Math.random()*150),
					v: Math.floor(Math.random()*150),
					w: Math.floor(Math.random()*150),
					x: Math.floor(Math.random()*150),
					y: Math.floor(Math.random()*150),
					z: Math.floor(Math.random()*150)
				}

				docw = $("body").width();
				doch = $("body").height();

				svgw = $("#mysvg").width();
				svgh = $("#mysvg").height();

				mdptx = svgw/2;
				mdpty = svgh/2;

				createPath();
			}, 10);

			function createPath() {
				$("#status").html("Document width: " + docw + "<br>Document height: " + doch + "<br>SVG width: " + svgw + "<br>SVG height: " + svgh + "<br>mx: " + mx + "<br>my: " + my + "<br>random: " + random.a + "<br>mx_rel_5: " + mx_rel_5 + "<br>mx_10_rel: " + mx_10_rel + "<br>mx_rel: " + mx_rel + "<br>mx_rel_5: " + mx_rel_5 + "<br>mx_rel_10: " + mx_rel_10);

/*
				var path1 = '<path d="M'+ mdptx +',' + mdpty + ' Q100,' + random.a + ' 150,50 T250,50 T350,50 T450,50 T' + (550+random.k) + ',' + (50+random.l) + '" stroke="#eee" stroke-width="7" fill="none" />';
				var path2 = '<path d="M'+ mdptx +',' + mdpty + ' Q100,' + random.b + ' 150,50 T250,50 T350,50 T450,50 T' + (550+random.j) + ',' + (50+random.m) + '" stroke="#eee" stroke-width="7" fill="none" transform="rotate(10 ' + mdptx + ' ' + mdpty + ')" />';
				var path3 = '<path d="M'+ mdptx +',' + mdpty + ' Q100,' + random.c + ' 150,50 T250,50 T350,50 T450,50 T' + (550+random.i) + ',' + (50+random.n) + '" stroke="#eee" stroke-width="7" fill="none" transform="rotate(20 ' + mdptx + ' ' + mdpty + ')" />';
				var path4 = '<path d="M'+ mdptx +',' + mdpty + ' Q100,' + random.d + ' 150,50 T250,50 T350,50 T450,50 T' + (550+random.h) + ',' + (50+random.o) + '" stroke="#eee" stroke-width="7" fill="none" transform="rotate(30 ' + mdptx + ' ' + mdpty + ')" />';
				var path5 = '<path d="M'+ mdptx +',' + mdpty + ' Q100,' + random.e + ' 150,50 T250,50 T350,50 T450,50 T' + (550+random.g) + ',' + (50+random.p) + '" stroke="#eee" stroke-width="7" fill="none" transform="rotate(40 ' + mdptx + ' ' + mdpty + ')" />';
				var path6 = '<path d="M'+ mdptx +',' + mdpty + ' Q100,' + random.f + ' 150,50 T250,50 T350,50 T450,50 T' + (550+random.f) + ',' + (50+random.q) + '" stroke="#eee" stroke-width="7" fill="none" transform="rotate(50 ' + mdptx + ' ' + mdpty + ')" />';
				var path7 = '<path d="M'+ mdptx +',' + mdpty + ' Q100,' + random.g + ' 150,50 T250,50 T350,50 T450,50 T' + (550+random.e) + ',' + (50+random.r) + '" stroke="#eee" stroke-width="7" fill="none" transform="rotate(60 ' + mdptx + ' ' + mdpty + ')" />';
				var path8 = '<path d="M'+ mdptx +',' + mdpty + ' Q100,' + random.h + ' 150,50 T250,50 T350,50 T450,50 T' + (550+random.d) + ',' + (50+random.s) + '" stroke="#eee" stroke-width="7" fill="none" transform="rotate(70 ' + mdptx + ' ' + mdpty + ')" />';
				var path9 = '<path d="M'+ mdptx +',' + mdpty + ' Q100,' + random.i + ' 150,50 T250,50 T350,50 T450,50 T' + (550+random.c) + ',' + (50+random.t) + '" stroke="#eee" stroke-width="7" fill="none" transform="rotate(80 ' + mdptx + ' ' + mdpty + ')" />';
				var path10 = '<path d="M'+ mdptx +',' + mdpty + ' Q100,' + random.j + ' 150,50 T250,50 T350,50 T450,50 T' + (550+random.b) + ',' + (50+random.u) + '" stroke="#eee" stroke-width="7" fill="none" transform="rotate(90 ' + mdptx + ' ' + mdpty + ')" />';
				var path11 = '<path d="M'+ mdptx +',' + mdpty + ' Q100,' + random.k + ' 150,50 T250,50 T350,50 T450,50 T' + (550+random.a) + ',' + (50+random.v) + '" stroke="#eee" stroke-width="7" fill="none" transform="rotate(100 ' + mdptx + ' ' + mdpty + ')" />';
*/


				/*
				var path2 = '<path d="M250,250 Q' + (350) + ',' + (random.b) + ' ' + (450) + ',250 T' + (500) + ',250 T' + (550) + ',250 T' + (600) + ',250 T' + (mx) + ',250" stroke="#eee" stroke-width="7" fill="none" />';
				var path3 = '<path d="M150,150 Q' + (250) + ',' + (random.a) + ' ' + (350) + ',200 T' + (450) + ',200 T' + (500) + ',200 T' + (550) + ',200 T' + 0 + ',' + (-mx) +'" stroke="#eee" stroke-width="7" fill="none" transform="rotate(45deg' + ' ' + mdptx + ' ' + mdpty + ')" />';
				*/
/*
				var path3 = '<path d="M250,200 Q300,' + (200+random.c) + ' 350,200 t100,0 t100,0 t100,0 t100,0" stroke="#eee" stroke-width="7" fill="none" />';

				var path4 = '<path d="M250,150 Q300,' + (200+random.d) + ' 350,150 t100,0 t100,0 t100,0 t100,0" stroke="#eee" stroke-width="7" fill="none" />';

				var path5 = '<path d="M250,100 Q300,' + (200+random.e) + ' 350,100 t50,-50 t50,0 t100,150 t100,-150" stroke="#eee" stroke-width="7" fill="none" />';
*/


				var path1 = '<path d="M' + mdptx + ' ' + mdpty + ' q' + mx_rel_10 + ',' + (-30+random.a) + ' ' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + (0+random.l) + '" stroke="#fafafa" stroke-width="7" fill="none" />';
				var path2 = '<path d="M' + mdptx + ' ' + mdpty + ' q' + mx_rel_10 + ',' + (-30+random.b) + ' ' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + (0+random.k) + '" stroke="#fafafa" stroke-width="7" fill="none" transform="rotate(-5 ' + mdptx + ' ' + mdpty + ')" />';
				var path3 = '<path d="M' + mdptx + ' ' + mdpty + ' q' + mx_rel_10 + ',' + (-30+random.c) + ' ' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + (0+random.j) + '" stroke="#fafafa" stroke-width="7" fill="none" transform="rotate(-10 ' + mdptx + ' ' + mdpty + ')" />';
				var path4 = '<path d="M' + mdptx + ' ' + mdpty + ' q' + mx_rel_10 + ',' + (-30+random.d) + ' ' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + (0+random.i) + '" stroke="#fafafa" stroke-width="7" fill="none" transform="rotate(-15 ' + mdptx + ' ' + mdpty + ')" />';
				var path5 = '<path d="M' + mdptx + ' ' + mdpty + ' q' + mx_rel_10 + ',' + (-30+random.e) + ' ' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + (0+random.h) + '" stroke="#fafafa" stroke-width="7" fill="none" transform="rotate(-20 ' + mdptx + ' ' + mdpty + ')" />';
				var path6 = '<path d="M' + mdptx + ' ' + mdpty + ' q' + mx_rel_10 + ',' + (-30+random.f) + ' ' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + (0+random.g) + '" stroke="#fafafa" stroke-width="7" fill="none" transform="rotate(-25 ' + mdptx + ' ' + mdpty + ')" />';
				var path7 = '<path d="M' + mdptx + ' ' + mdpty + ' q' + mx_rel_10 + ',' + (-30+random.g) + ' ' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + (0+random.f) + '" stroke="#fafafa" stroke-width="7" fill="none" transform="rotate(-30 ' + mdptx + ' ' + mdpty + ')" />';
				var path8 = '<path d="M' + mdptx + ' ' + mdpty + ' q' + mx_rel_10 + ',' + (-30+random.h) + ' ' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + (0+random.e) + '" stroke="#fafafa" stroke-width="7" fill="none" transform="rotate(-35 ' + mdptx + ' ' + mdpty + ')" />';
				var path9 = '<path d="M' + mdptx + ' ' + mdpty + ' q' + mx_rel_10 + ',' + (-30+random.i) + ' ' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + (0+random.d) + '" stroke="#fafafa" stroke-width="7" fill="none" transform="rotate(-40 ' + mdptx + ' ' + mdpty + ')" />';
				var path10 = '<path d="M' + mdptx + ' ' + mdpty + ' q' + mx_rel_10 + ',' + (-30+random.j) + ' ' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + (0+random.c) + '" stroke="#fafafa" stroke-width="7" fill="none" transform="rotate(-45 ' + mdptx + ' ' + mdpty + ')" />';
				var path11 = '<path d="M' + mdptx + ' ' + mdpty + ' q' + mx_rel_10 + ',' + (-30+random.k) + ' ' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + (0+random.b) + '" stroke="#fafafa" stroke-width="7" fill="none" transform="rotate(-50 ' + mdptx + ' ' + mdpty + ')" />';
				var path12 = '<path d="M' + mdptx + ' ' + mdpty + ' q' + mx_rel_10 + ',' + (-30+random.l) + ' ' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + (0+random.a) + '" stroke="#fafafa" stroke-width="7" fill="none" transform="rotate(-55 ' + mdptx + ' ' + mdpty + ')" />';

				var path13 = '<path d="M' + mdptx + ' ' + mdpty + ' q' + mx_rel_10 + ',' + (-30+random.l) + ' ' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 + ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + 0 +  ' ' + 't' + mx_rel_5 + ',' + (0+random.a) + '" stroke="#fafafa" stroke-width="7" fill="none" transform="rotate(-180 ' + mdptx + ' ' + mdpty + ')" />';
				//$("#mysvg").html(path1 + path2 + path3 + path4 + path5 + path6 + path7 + path8 + path9 + path10 + path11);
				$("#mysvg").html(path1 + path2 + path3 + path4 + path5 + path6 + path7 + path8 + path9 + path10 + path11 + path12 + path13);
			}
		});
	</script>
</body>
</html>
