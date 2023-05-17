# bertoti
 Repositório da disciplina de Engenharia de Software I do prof. Giuliano Bertoti
 
 Aula 1 - 17/02/23
 
We see three critical differences between programming and software engineering: time, scale, and the trade-offs at play. On a software engineering project, engineers need to be more concerned with the passage of time and the eventual need for change. In a software engineering organization, we need to be more concerned about scale and efficiency, both for the software we produce as well as for the organization that is producing it. Finally, as software engineers, we are asked to make more complex decisions with higher-stakes outcomes, often based on imprecise estimates of time and growth.

Aula 2-23/02/23

Within Google, we sometimes say, “Software engineering is programming integrated over time.” Programming  is certainly a significant part of software engineering: after all, programming is how you generate new software in the first place. If you accept this distinction, it also becomes clear that we might need to delineate between programming tasks (development) and software engineering tasks (development, modification, maintenance). The addition of time adds an important new dimension to programming. Cubes aren’t squares, distance isn’t velocity. Software engineering isn’t programming.

Engenharia de Software pode ser definida como um conjunto de ações necessárias para o desenvolvimento de uma aplicação, independente da plataforma utilizada. Como citado no texto acima, a engenharia de software não é definida apenas pela programação (sendo esta apenas uma parte do processo), pois é necessário conhecimento teórico, bem como análise, coleta e processamento de dados, identificar possíveis erros nos produtos desenvolvidos, bem como saber como se comunicar com o cliente de forma a desenvolver a melhor solução possível. Todo engenheiro de software pode atuar como programador, porém nem todo programador possuí todos os atributos necessários para ser um engenheiro de software. 

Aula 3-24/02/23

1-O que é Engenharia de Software?
2-O que são requisitos?
2.1- O que são requisitos funcionais?
2.2-O que são requisitos não funcionais?
Dê exemplos.

DESAFIO- Escreva 2 exemplos de trade-offs envolvendo requisitos não funcionais.

Aula 4- 24/03/23

Classe UML

![Diagrama em branco - Classe UML](https://github.com/Hugohs98/bertoti/assets/111614142/73fc6fa6-3b35-455c-bbf6-b16293170bcf)

Código:

CLASSE CURSO:

public class Curso {
    private int numero;
    private String nome;
    private List<Disciplina> lista;
    
    public Curso (int numero, String nome) {
        this.numero = numero;
        this.nome = nome;
        lista = new ArrayList<Disciplina>();
    }
    
    public void adicionaDisciplina(Disciplina disciplina) {
        lista.add(disciplina);
    }
    
    public void imprimir(){
        System.out.println("Curso:" + nome);
        System.out.println("Numero:" + numero);
        
        System.out.println("Disciplinas:");
        for (int i = 0; i < lista.size(); i++) {
            Disciplina disciplina = lista.get(i);
            System.out.print("*");
            disciplina.imprime();                    
        }
    }
    
    public int calculaTotalHora() {
        int total = 0;
        for (int i = 0; i<lista.size(); i++) {
            Disciplina disciplina = lista.get(i);
            total = total + disciplina.calcularHora();     
        }
        System.out.println("A carga horária total é:" + total);
        return total;
    }
    
    public int exibeMaiorCargaHoraria() {
        int max = 0;
        for (Disciplina disciplina : lista) {
            if(disciplina.calcularHora() > max) {
                max = disciplina.calcularHora();
            }    
        }
        System.out.println("A maior carga horária é de:" + max);
        return max;    
    }
}
 
 ---------------------------------------------------------------------------------------
 
 CLASSE DISCIPLINA:
 
 public class Disciplina {
    private String nome;
    private int codigo;
    private int cargaHoraria;
    
    public Disciplina (String nome, int codigo, int cargaHoraria) {
        this.nome = nome;
        this.codigo = codigo;
        this.cargaHoraria = cargaHoraria;
    }
    
    public void imprime(){
        System.out.println("Disciplina:" + nome);
        System.out.println("Código:" + codigo);
        System.out.println("Carga Horária:" + cargaHoraria);
    }
    
    public int calcularHora() {
        return cargaHoraria;
    }
}

 ---------------------------------------------------------------------------------------
 
 CLASSE MAIN TESTE:
 
 public class Proj_Curso {
 
    public static void main(String[] args) {
        Disciplina d1, d2, d3, d4;
        d1 = new Disciplina("Linguagens de programação", 100, 20);
        d2 = new Disciplina("Matemática discreta", 102, 40);
        d3 = new Disciplina("Calculo", 103, 40);
        d4 = new Disciplina("Engenharia de Software", 104, 60);
        
        Curso ads = new Curso(1234, "Análise de Sistemas");
        
        ads.adicionaDisciplina(d1);
        ads.adicionaDisciplina(d2);
        ads.adicionaDisciplina(d3);
        ads.adicionaDisciplina(d4);
        ads.imprimir();
        ads.calculaTotalHora();
        ads.exibeMaiorCargaHoraria();
        
    }
    
}
