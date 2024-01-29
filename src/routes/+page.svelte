<script>
    function zerteilung(){
        let splits
        let ergebnis=0
        let letzes_rechen_zeichen= 1
        let letzte_berechnung_wert_array = 2
        let anzahl_rechenoperationen_array
        let position_mal
        let position_zeichen_vor_mal
        let position_zeichen_nach_mal
        let position_zeichen_vor_durch, position_zeichen_nach_durch
        let position_durch
    
        kontrolle = 2
        
        splits= wert.split(" ")
        anzahl_rechenoperationen_array = splits.length /2
        
        if(splits.find(() =>'*' )){
            position_mal = splits.find(() =>'*')
            position_zeichen_vor_mal =parseFloat(position_mal) -1 
            position_zeichen_nach_mal = position_zeichen_vor_mal + 2
            ergebnis = position_zeichen_vor_mal * position_zeichen_nach_mal
        }
        if(splits.find(() =>'/' )){
            position_durch = splits.find(() =>'/')
            position_zeichen_vor_durch =parseFloat(position_durch) -1 
            position_zeichen_nach_durch = position_zeichen_vor_durch + 2
            ergebnis = position_zeichen_vor_durch / position_zeichen_nach_durch
        }
        switch (splits[1]) {
      case  '+':
            ergebnis=parseFloat(splits[0]) + parseFloat(splits[2])
            break;
      case '-':
             ergebnis=parseFloat(splits[0]) - parseFloat(splits[2])
             break;
      case '*':
             ergebnis=parseFloat(splits[0]) * parseFloat(splits[2])
             break;
      case '/':
             ergebnis=parseFloat(splits[0]) / parseFloat(splits[2])
             break;
    }
    
    while (kontrolle < anzahl_rechenoperationen_array){
    switch (splits[letzes_rechen_zeichen+2]) {
      case  '+':
             ergebnis= ergebnis + parseFloat(splits[letzte_berechnung_wert_array+2])
             break;
      case '-':
             ergebnis= ergebnis - parseFloat(splits[letzte_berechnung_wert_array+2])
             break;
      case '*':
             ergebnis= ergebnis * parseFloat(splits[letzte_berechnung_wert_array+2])
             break;
      case '/':
             ergebnis= ergebnis / parseFloat(splits[letzte_berechnung_wert_array+2])
             break;
    }
    kontrolle = kontrolle +1
    letzes_rechen_zeichen = letzes_rechen_zeichen +2
    letzte_berechnung_wert_array = letzte_berechnung_wert_array +2 
    }
    
        console.log(ergebnis)
        wert = ergebnis.toString()
      automatic_delete_control = 1
    }
    function AC(){
        wert = ""
    
    } 
    function DEL() {
        wert = wert.trim()
        wert = wert.substring(0, wert.length-1)
        wert = wert.trim()
    
    }
    function test(input){
       
    
        if (automatic_delete_control == 1){
            wert = ""
            automatic_delete_control = 0
        }
        wert = wert + input
        console.log(wert)
        
    }
    let button;
    let wert = "";
    let input;
    let kontrolle = 2
    let automatic_delete_control = 0
    
    
    
    
    
    
    </script>
    
    <h1>Welcome to Web-Taschenrachner</h1>
    
    <input type="text" id="Ausgabefeld" bind:value={wert}>
    
    <table>
        <tbody>
          <tr>
            <td> <button on:click={() => test('7')}> 7</button></td>
            <td> <button on:click={() => test('8')}> 8</button></td>
            <td> <button on:click={() => test('9')}> 9</button></td>
            <td> <button on:click={() => test(' + ')}> +</button></td>
          </tr>
          <tr>
            <td> <button on:click={() => test('4')}> 4</button></td>
            <td> <button on:click={() => test('5')}> 5</button></td>
            <td> <button on:click={() => test('6')}> 6</button></td>
            <td> <button on:click={() => test(' - ')}> -</button></td>
          </tr>
          <tr>
            <td> <button on:click={() => test('1')}> 1</button></td>
            <td> <button on:click={() => test('2')}> 2</button></td>
            <td> <button on:click={() => test('3')}> 3</button></td>
            <td> <button on:click={() => test(' * ')}> *</button></td>
          </tr>
          <tr>
            <td> <button on:click={() => test('(')}> (</button></td>
            <td> <button on:click={() => test('0')}> 0</button></td>
            <td> <button on:click={() => test(')')}> )</button></td>
            <td> <button on:click={() => test(' / ')}> /</button></td>
          </tr>
          <tr>
            <td> <button on:click={() => AC()}> AC</button></td>
            <td> <button on:click={() => test('.')}> .</button></td>
            <td> <button on:click={() => DEL()}> DEL </button></td>
            <td> <button on:click= {()=> zerteilung()}> =</button></td>
          </tr>
        </tbody>
      </table>
      <style> 
        table, tr {
      border: 1px solid;
      width: 500px;
      height:105px
    }
      button {
        width:125px;
        height:105px;
      }
      input{
        width: 512px;
        height: 105px;
    
    
      }
    </style>