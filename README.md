pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});


pm.test("Scope value is as expected", function () {
    pm.response.to.have.jsonBody("scope","APP");  
});

pm.test("Status value is as expected", function () {
    pm.response.to.have.jsonBody("status","OK");  
});


pm.test("Server is as expected", function () {
    pm.response.to.have.hea
    
    
    
    pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Address added successfully", function () {
    pm.expect(pm.response.text()).to.include("Address successfully updated");
});


pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});



pm.expect(pm.response.json().address).to.equal(pm.collectionVariables.get("updateAddress"));


{
"name":"{{BookName}}",
"isbn":"{{ISBN}}",
"aisle":"{{Aisle}}",
"author":"{{Author Name}}"
}





pm.environment.set("ID", pm.response.json().ID);

pm.test("Book is Successfully Added", function () {
    pm.response.to.have.jsonBody("Msg","successfully added");
});




pm.test("Book Name working as expected by Author Name", function () {
  var data = JSON.parse(responseBody);
pm.expect(data[0].book_name).to.equal(pm.collectionVariables.get("BookName"));
    
});
