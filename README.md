﻿// AtividadeAgenda4Ano

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        // Array para armazenamento dos contatos
var contatos = [];

function adicionarContato() {
    var name = document.getElementById("name").value;
    var phone = document.getElementById("phone").value;

    // Verifica se os campos foram preenchidos
    if(name && phone) {
        var contato = {
        nome: name,
        telefone: phone
        };

        contatos.push(contato);
        exibirContatos();
    }

    // Limpa os campos após adicionar o contato
    document.getElementById("name").value = "";
    document.getElementById("phone").value = "";
}

function buscarContato() {
    var searchName = document.getElementById("searchName").value;

    var contato = contatos.find(function(item) {
    // Procurar pelo contato com o nome digitado
    return item.nome === searchName;
});

    if(contato){
        alert("Nome: " + contato.nome + "\nTelefone: " + contato.telefone);
    }else {
        alert("Nome não encontrado.");
    }

    // Limpar o campo de busca
    document.getElementById("searchName").value = "";
}

function exibirContatos() {
    var contactList = document.getElementById("contactList");
    contactList.innerHTML = "";

    // Exibir todos os contatos na lista
    contatos.forEach(function(item) {
        var li = document.createElement("li");
        li.textContent = "Nome: " + item.nome + ", Telefone: " + item.telefone;
        contactList.appendChild(li);
});
}

function removerContato() {
    var removeName = document.getElementById("removeName").value

    for(var i =0; i< contatos.length; i++) {
        if(contatos[i].nome === removeName){
            contatos.splice(i, 1) // remove o contato do array
            break
        }
    }
    exibirContatos();
}

function atualizarContato() {
    var updateName = document.getElementById("updateName").value;
    var updatePhone = document.getElementById("updatePhone").value;

    var contato = contatos.find(function(item) {
        return item.telefone === updatePhone;
    });

    if (contato) {
        contato.nome = updateName;
        contato.telefone = updatePhone;
        exibirContatos();
    }

    document.getElementById("updateName").value = "";
    document.getElementById("updatePhone").value = "";
}


function prepararAtualizacao(numero) {
    var contato = contatos.find(function(item) {
        return item.telefone === numero;
    });

    if (contato) {
        document.getElementById("updateName").value = contato.nome;
        document.getElementById("updatePhone").value = contato.telefone;
        atualizarContato(contato);
    }
}

    </script>
</head>
<body>
    <h1>Gerenciador de Contatos</h1>

    <h2>Adicionar Contato</h2>
    <label for="name">Nome:</label>
    <input type="text" id="name" placeholder="Nome">
    <br>
    <label for="phone">Telefone:</label>
    <input type="tel" id="phone" placeholder="Telefone">
    <br>
    <button onclick="adicionarContato()">Adicionar</button>

    <h2>Buscar Nome</h2>
    <label for="searchName">Nome:</label>
    <input type="text" id="searchName" placeholder="Nome">
    <br>
    <button onclick="buscarContato()">Buscar</button>

    <h2>Lista de Contatos</h2>
    <ul id="contactList"></ul>

    <h2>Remover Contato</h2>
    <label for="removeName">Nome:</label>
    <input type="text" id="removeName" placeholder="Nome">
    <br>
    <button onclick="removerContato()">Remover</button>

    <h2>Atualizar Contato</h2>
    <label for="updateName">Nome:</label>
    <input type="text" id="updateName" placeholder="Nome">
    <br>
    <label for="updatePhone">Telefone:</label>
    <input type="tel" id="updatePhone" placeholder="Telefone">
    <br>
    <button onclick="atualizarContato()">Atualizar</button>



</body>
</html>
