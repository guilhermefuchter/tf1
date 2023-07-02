# tf1

<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Exemplo de Interação com API</title>
    <style>
       
        body {
            font-family: Arial, sans-serif;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            padding: 20px;
        }

      


        

        #user-info {
            border: 2px solid #ccc;
            padding: 40px;
            margin-bottom: 40px;
        }

        #user-info img {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            margin-bottom: 10px;
        }

        #btn-generate {
            padding: 10px 20px;
            background-color: blue;
            border: none;
            color: gray;
            cursor: pointer;
        }

        #btn-generate:hover {
            background-color: #00e1ff;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Informações de Usuário</h1>
        <div id="user-info"></div>
        <button id="btn-generate">Gerar Usuário</button>
    </div>



    <script>
      
        function fetchUser() {
            fetch('https://randomuser.me/api/')
                .then(response => response.json())
                .then(data => {
                    const user = data.results[0];
                    const fullName = `${user.name.first} ${user.name.last}`;
                    const email = user.email;
                    const picture = user.picture.large;

                    const userInfo = document.getElementById('user-info');
                    userInfo.innerHTML = `
                        <img src="${picture}" alt="${fullName}">
                        <h2>${fullName}</h2>
                        <p>Email: ${email}</p>
                    `;
                })
                .catch(error => {
                    console.log('Erro ao obter dados do usuário:', error);
                });
        }

       
        document.getElementById('btn-generate').addEventListener('click', fetchUser);

        
        fetchUser();
    </script>
</body>
</html>
