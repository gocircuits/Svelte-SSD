
<script>
    import { onMount } from "svelte";
	
		let search = ""
		let neighborhood = "williamsburg";
		let curName = "";
		let firstComment = "";

//     const apiURL = "https://spreadsheets.google.com/feeds/list/1MgyQc9fiozPEurk-5OtqUdq6rIDTpMpDEKpqJQhHSlo/od6/public/values?alt=json";
		    const apiURL = "https://spreadsheets.google.com/feeds/list/1m9_xfXzoPs6MP3Rz1J27lVVUg7Rnf320ODLZ5pV0ADs/od6/public/values?alt=json";
    let data = [];
		let dataArr = []
	
	onMount(async function() {
        const response = await fetch(apiURL);
        data = await response.json();
				dataArr = data.feed.entry;
				//console.log(data);
				console.log(dataArr[1].gsx$date.$t);
    });

</script>

		<div class="nav">
				<h2 class="logo" align="center">
					Springs Sunday Dances
			</h2>
		</div>

<div class="search-container">
		<input class="searchbox" type="text" name="search" bind:value={search} placeholder="search for caller"/>
</div>
		<div class="container">
<p>
			</p><p>
			</p>
{#each dataArr as item }
	<div class="box">
			<p>
			{item.gsx$date.$t}
			</p>
		<div class="info">

							<p><b> Dance: {item.gsx$title.$t} </b></p>
								<p> caller: {item.gsx$caller.$t} </p>
								<p> cuer: {item.gsx$cuer.$t} </p>
						</div>
			</div>
{/each}
		
	
</div>


<style>
@import url('https://fonts.googleapis.com/css2?family=Kiwi+Maru:wght@300&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Inconsolata:wght@300;500&display=swap');
	p {
		font-family:Kiwi+Maru;
		font-weight:200;
		color:#000;
	}
	
	.container {
		width:99%;
		height: auto;
		margin: 50 20 20 20;
		background-color:#000;
	}
	.searchbox {
		position:relative;
		display: inline-block;
		margin-top:15px;
		padding-left:30px;
		color: #fff;
		width: 50%;
		height: 60px;
		border-radius:20px;
		background-color:#3a3a3a;
		text-align:left;
		margin-bottom: 15px;
	}
	::placeholder {
  	color: #bbb;
		font-family:Kiwi+Maru;
		font-weight:400;
	
}
	.nav {
		float:left;
/* 		position: fixed; */
		text-align: left;
		width: 96%;
		height: 38pt;
		border: none;
		padding: 0px;
		margin-top: 0px;
		background-color:#FFF;
		box-shadow: 1px 1px 5px #aaa;
		overflow:hidden;
		display: inline-block;
	}
	.logo {
		;position:relative;
		font-family:Inconsolata;
		font-weight:100;
		top: -10px;
	}
	.info {
		position:relative;
		float: right;
		width:90%;
		height:50%;
		text-align:left;
		padding-right:10px;
		padding-left:50px;
		bottom:0;
		color:#EEE;
		background-color:transparent;
		opacity: 0.93;
		display:inline-block;
	}
	.box {
		float:left;
		text-align: left;
		height: auto;
		width: 40%;
		padding-left: 10px;
		padding-right: 10px;
		padding-top: 10px;
		margin-bottom: 10px;
		margin-right:5px;
		border: .5pt solid #8AC3F3;
		background-color:#8DDFFC;
		box-shadow: 1px 1px 5px #aaa;
		overflow:hidden;
		display: inline-block;
	}
	.searchbox {
		height: 40px;
		margin-left:5px;
		outline: none;
	}

	
</style>