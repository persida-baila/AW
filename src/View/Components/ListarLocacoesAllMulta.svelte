
<script>
  import { listarLocacoes } from "../../Controllers/LocacaoController";
  
  const listaLocacoes = listarLocacoes;
  
</script>

<body style="background-color: rgb(27, 8, 27);">
    <aside class = "listarL">
        <fieldset>
            <legend>Listar Locações Com Multa</legend>
            <table>
                <thead>
                    
                    <tr>
                        <th>Nome</th>
                        <th>Filme</th>
                        <th>Data do Aluguer</th>
                        <th>Data de Entrega</th>
                    </tr>
                </thead>
                <tbody>
                  {#await listaLocacoes()}
                  <tr>
                 <td colspan="4">Carregando...</td> 
                </tr>
                {:then locacoes} 
                  {#each locacoes.filter(({ multa }) => multa) as locacao}
                    <tr>
                      <td>{locacao.nome}</td>
                      <td>{locacao.titulo}</td>
                      <td>{locacao.dataAluguer}</td>
                      <td>{locacao.dataEntrega}</td>
                    </tr>
                    {/each}
                {/await}
                </tbody>
            </table>
        </fieldset>
    </aside>
    </body>
    <style>
        .listarL{
      
       padding: 1rem 2rem;
       margin: 5rem 2rem;
       border-radius: 1.5rem;
       background-color: rgb(146, 1, 122);
       align-items: stretch;
       color: white;
       font-weight: 600;
     }
     table{
     background-color: rgb(146, 1, 122);
     border-radius: 0.2rem;
     margin-top: 1rem ;
     min-width: 20rem;
     color: white;
   }
   th{
      
      background-color: rgb(70, 22, 70);
   }
     
     fieldset{
       border-radius: 0.2rem;
       border: rgb(146, 1, 122);
     }
   </style>