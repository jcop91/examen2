# examen2

----------------------------------------

exports.handler = async (event) => {
    
    let historial = event.historial_clinico;
    let nombre = event.nombre;
    let curp = event.curp;
    let edad = event.edad;
    let ocupacion = event.ocupación;
    
    var xhttp = new XMLHttpRequest();
        xhttp.onreadystatechange = function () {
            if (this.readyState == 4 && this.status == 200) {
                //this.responseText
                 const response = {
                     statusCode: 200,
                     body: JSON.stringify(this.responseText),
                     };
                return response;
                
            }
        };
        xhttp.open("POST", "http://ortiz-examen-nlu.eu-gb.mybluemix.net/toneAnalyzer", true);
        xhttp.setRequestHeader("Content-type", "application/json");
        xhttp.send(JSON.stringify({
            "text": historial
        }));
};
