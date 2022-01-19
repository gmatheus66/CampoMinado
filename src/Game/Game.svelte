<script>
  import { library } from '@fortawesome/fontawesome-svg-core';
  import { faBomb } from '@fortawesome/free-solid-svg-icons';
  import { FontAwesomeIcon} from 'fontawesome-svelte';

  library.add(faBomb);
  const casas = 10;
  let maxNBombs = 10;
  let minNBombs = 3;
  let dadCells;
  let bombs;


  let init = () => {
    dadCells = Array.from(Array(casas), () => new Array(casas));
    bombs = generateBombs();
    populateDad();
    populateBombs();
    populateTips(); 

  }

  let nBombs = () => {
    return Math.floor(Math.random() * (maxNBombs - minNBombs + 1) + minNBombs);
  };
  
  let numberBombs = nBombs();
  

  function populateDad () {
    for(let i = 0; i < dadCells.length; i++){
      for(let x = 0; x < dadCells[i].length; x++){
        dadCells[i][x] = 0;
      }
    }
  }

  let populateBombs = () => {
      for (const bomb of bombs) {
        if(dadCells[bomb.x] != undefined && dadCells[bomb.x][bomb.y] != undefined){
          dadCells[bomb.x][bomb.y] = "*";
        }
      }
  };
  

  function generateBombs (){
    return Array.from(Array(numberBombs), () => new Object({x: locateBombs(), y: locateBombs()}) );
  }

  function populateTips (){
    for(const bb of bombs){
      if(dadCells[bb.x][bb.y - 1] != undefined && dadCells[bb.x][bb.y - 1] != "*"){
        dadCells[bb.x][bb.y - 1]++;
      }
      if(dadCells[bb.x][bb.y+1] != undefined && dadCells[bb.x][bb.y+1] != "*"){
        dadCells[bb.x][bb.y+1]++;
      }
      
      if(bb.x > 0){
        if(dadCells[bb.x - 1][bb.y+1] != undefined && dadCells[bb.x - 1][bb.y + 1] != "*"){
          dadCells[bb.x - 1][bb.y+1]++;
        }
        if(dadCells[bb.x - 1][bb.y] != undefined && dadCells[bb.x-1][bb.y] != "*" ){
          dadCells[bb.x - 1][bb.y]++;
        }
        if(dadCells[bb.x - 1][bb.y - 1] != undefined && dadCells[bb.x - 1][bb.y - 1] != "*"){
          dadCells[bb.x - 1][bb.y - 1 ]++;
        }
      }

      if(bb.x < (casas - 1)){
        if(dadCells[bb.x + 1][bb.y + 1] != undefined && dadCells[bb.x + 1][bb.y + 1] != "*"){
          dadCells[bb.x + 1][bb.y + 1]++;
        }
        if(dadCells[bb.x + 1][bb.y] != undefined && dadCells[bb.x + 1][bb.y] != "*"){
          dadCells[bb.x + 1][bb.y]++;
        }
        if(dadCells[bb.x + 1][bb.y - 1] != undefined && dadCells[bb.x + 1][bb.y - 1] != "*"){
          dadCells[bb.x + 1][bb.y - 1]++;
        }

      }


      };

  }

  let locateBombs = () => {
    return Math.floor(Math.random() * ((casas-1) - 0 + 1) + 0);
  };

  let changeBlock = (cell) => {
    console.log("Click", cell);
    
  };

  init();
</script>

<h2>Game</h2>

<table>
  {#each dadCells as dc, dcI}
    <tr>
      {#each dc as sc, scI}
        <td on:click|preventDefault={() => changeBlock(sc)}>
        {#if sc == "*"}
        <FontAwesomeIcon icon={faBomb} />
        {:else}
          {sc}
        {/if}
        </td>
      {/each}
    </tr>
  {/each}
</table>

<style>


  h2 {
	color: #fff;
  }
  table {
   position: absolute;
   margin-left: 35%;
   bottom: 5%;
   background-color: rgb(31, 31, 31);
   border-radius: 5px;
   padding: 5px;
   border: 2px solid #5fe36a;
  }

  td {
   background-color: #fff;
   width: 25px;
   height: 35px;
   font-size: 25px;
   cursor: pointer;
   border: none;
   color: rgb(31, 31, 31);
   text-align: center;
  }
</style>

