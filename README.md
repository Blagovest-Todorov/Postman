# Postman API Test Example
using postman UI testuing


pm.test("Status code 200 OK", function() {
pm.response.to.have.status(200)
})

pm.test("Response is a valid array of issues", function() {
    pm.expect(pm.response.headers.get('Content-Type')).to.eql('application/json; charset=utf-8');   
    const json = pm.response.json(); 
    pm.expect(Array.isArray(json)).equals(true);   

    for(let item of json){
        pm.expect(typeof(item)).equals("object");
        pm.expect(Number.isInteger(item.id)).equals(true);
        pm.expect(typeof(item.title)).equals("string");
        pm.expect(typeof(item.body)).equals("string");
    }
})
