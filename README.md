# examen2

----------------------------------------

const https = require('https');

exports.handler = async (event) => {
    
    let historial = event.historial_clinico;
    let nombre = event.nombre;
    let curp = event.curp;
    let edad = event.edad;
    let ocupacion = event.ocupacion;
    
    const data = JSON.stringify({
        "text": historial
    });
    
    const options = {
        hostname: 'https://api.eu-gb.natural-language-understanding.watson.cloud.ibm.com/instances/f0f8edda-af29-4075-a8f7-eea14df40262/v1/analyze?version=2021-03-25',
        port: 80,
        path: '/',
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
            'Content-Length': data.length,
        },
        
    };
    
    const req = https.request(options, (res) => {
        console.log(`statusCode: ${res.statusCode}`)
        
        
        res.on('data', (d) => {
            process.stdout.write(d)
            
            
        })
    });
    
    req.on('error', (error) => {
        console.error(error)
    });
    
   const response = {
                     statusCode: 200,
                     body: req,
                     };
    
    req.end();
    return response;
    
};

