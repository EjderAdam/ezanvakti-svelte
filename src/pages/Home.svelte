<script lang="ts">
	import axios from "axios";
	var kalan = "yukleniyor";
	var now = Date.now(),
		imsak = "yukleniyor",
		gunes = "yukleniyor",
		ogle = "yukleniyor",
		ikindi = "yukleniyor",
		aksam = "yukleniyor",
		yatsi = "yukleniyor",
		siradakiName = "yukleniyor",
		siradakiTime = 0;

	axios
		.get("https://ezanvakti.herokuapp.com/vakitler/9716")
		.then((response) => {
			imsak = response.data[0].Imsak;
			gunes = response.data[0].GunesDogus;
			ogle = response.data[0].Ogle;
			ikindi = response.data[0].Ikindi;
			aksam = response.data[0].Aksam;
			yatsi = response.data[0].Yatsi;
			reloadSiradaki();
			setInterval(() => {
				now = Date.now();
				let distance = siradakiTime - now;
				kalan = `${Math.floor(
					(distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
				)}:${Math.floor(
					(distance % (1000 * 60 * 60)) / (1000 * 60)
				)}:${Math.floor((distance % (1000 * 60)) / 1000)}`;
				if (siradakiTime <= Date.now()) {
					reloadSiradaki();
				}
			}, 1000);
		});
	function reloadSiradaki() {
		if (now < strToDate(imsak)) {
			siradakiName = "imsak";
			console.log("imsak");
			siradakiTime = strToDate(imsak);
		} else if (now < strToDate(gunes)) {
			siradakiName = "gunes";
			console.log("gunes");
			siradakiTime = strToDate(gunes);
		} else if (now < strToDate(ogle)) {
			siradakiName = "ogle";
			console.log("ogle");
			siradakiTime = strToDate(ogle);
		} else if (now < strToDate(ikindi)) {
			siradakiName = "ikindi";
			console.log("ikindi");
			siradakiTime = strToDate(ikindi);
		} else if (now < strToDate(aksam)) {
			siradakiName = "aksam";
			console.log("aksam");
			siradakiTime = strToDate(aksam);
		} else if (now < strToDate(yatsi)) {
			siradakiName = "yatsi";
			console.log("yatsi");
			siradakiTime = strToDate(yatsi);
		} else {
			siradakiName = "error";
			console.error("ererrrrrrrrrrrrorrrr");
		}
	}
	function strToDate(str: string) {
		var now = new Date();
		now.setHours(Number(str.substring(0, 2)));
		now.setMinutes(Number(str.substring(3, 5)));
		return now.getTime();
	}
</script>

<div class="aylik">
	<table style="margin: auto;">
		<tbody>
			<tr id="row1" class="renk">
				<td class="grbg">İmsak</td>
				<td class="grbg" id="imsak">{imsak}</td>
			</tr>
			<tr id="row2">
				<td>Güneş</td>
				<td id="gunes">{gunes}</td>
			</tr>
			<tr id="row3">
				<td class="grbg">Öğle</td>
				<td class="grbg" id="ogle">{ogle}</td>
			</tr>
			<tr id="row4">
				<td>İkindi</td>
				<td id="ikindi">{ikindi}</td>
			</tr>
			<tr id="row5">
				<td class="grbg">Akşam</td>
				<td class="grbg" id="aksam">{aksam}</td>
			</tr>
			<tr id="row6">
				<td>Yatsı</td>
				<td id="yatsi">{yatsi}</td>
			</tr>
			<tr id="row7">
				<td class="grbg kalan">Kalan</td>
				<td class="grbg kalan" id="kalan">{kalan}</td>
			</tr>
		</tbody>
	</table>
</div>

<style>
	.renk {
		background-color: darkgreen;
		color: azure;
	}

	table {
		margin: auto;
		padding-top: 10px;
		margin-top: 50px;
		max-width: 670px;
		font-family: "Courier New", Courier, monospace;
		border-radius: 10px;
	}

	td {
		border-radius: 7px;
		text-align: center;
		height: 40px;
		width: 150px;
	}

	.grbg {
		background-color: rgba(76, 149, 108, 0.555);
	}

	.kalan {
		border: 3px;
		border-style: ridge;
		border-color: blue;
	}
</style>
