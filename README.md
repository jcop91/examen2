# examen2

----------------------------------------

exports.handler = async (event) => {
    
    let historial = event.historial_clinico;
    let nombre = event.nombre;
    let curp = event.curp;
    let edad = event.edad;
    let ocupacion = event.ocupacion;
    
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
        xhttp.open("POST", "https://api.eu-gb.natural-language-understanding.watson.cloud.ibm.com/instances/f0f8edda-af29-4075-a8f7-eea14df40262", true);
        xhttp.setRequestHeader("Content-type", "application/json");
        xhttp.send(JSON.stringify({
            "text": historial
        }));
};
