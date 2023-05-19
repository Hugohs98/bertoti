# bertoti
 Repositório da disciplina de Engenharia de Software I do prof. Giuliano Bertoti
 
 Aula 1 - 17/02/23
 
We see three critical differences between programming and software engineering: time, scale, and the trade-offs at play. On a software engineering project, engineers need to be more concerned with the passage of time and the eventual need for change. In a software engineering organization, we need to be more concerned about scale and efficiency, both for the software we produce as well as for the organization that is producing it. Finally, as software engineers, we are asked to make more complex decisions with higher-stakes outcomes, often based on imprecise estimates of time and growth.

A programação está mais focada na implementação de código, enquanto a engenharia de software envolve preocupações adicionais, como gerenciamento de tempo, necessidade de mudanças, escala e eficiência. Os engenheiros de software lidam com decisões complexas e de alto risco, com base em estimativas imprecisas de tempo e crescimento.

Aula 2-23/02/23

Within Google, we sometimes say, “Software engineering is programming integrated over time.” Programming  is certainly a significant part of software engineering: after all, programming is how you generate new software in the first place. If you accept this distinction, it also becomes clear that we might need to delineate between programming tasks (development) and software engineering tasks (development, modification, maintenance). The addition of time adds an important new dimension to programming. Cubes aren’t squares, distance isn’t velocity. Software engineering isn’t programming.

Engenharia de Software pode ser definida como um conjunto de ações necessárias para o desenvolvimento de uma aplicação, independente da plataforma utilizada. Como citado no texto acima, a engenharia de software não é definida apenas pela programação (sendo esta apenas uma parte do processo), pois é necessário conhecimento teórico, bem como análise, coleta e processamento de dados, identificar possíveis erros nos produtos desenvolvidos, bem como saber como se comunicar com o cliente de forma a desenvolver a melhor solução possível. Todo engenheiro de software pode atuar como programador, porém nem todo programador possuí todos os atributos necessários para ser um engenheiro de software. 

Aula 3-24/02/23

1-O que é Engenharia de Software? <br/>
Engenharia de Software é uma disciplina que se dedica ao desenvolvimento sistemático e eficiente de software, abrangendo atividades como análise, projeto, implementação, teste e manutenção de sistemas de software. <br/>
2-O que são requisitos? <br/>
Requisitos são especificações e descrições das funcionalidades, características e restrições de um sistema de software que devem ser atendidas para satisfazer as necessidades dos usuários e das partes interessadas envolvidas no projeto. <br/>
2.1- O que são requisitos funcionais? <br/>
Requisitos funcionais são aqueles que descrevem as funcionalidades e o comportamento do sistema, ou seja, o que o sistema deve fazer. Eles definem as ações que o sistema deve executar em resposta a determinadas entradas e condições. Exemplo: "O sistema de uma loja online deve permitir que os usuários adicionem produtos ao carrinho de compras e realizem o pagamento." <br/>
2.2-O que são requisitos não funcionais? <br/>
Requisitos não funcionais são aqueles que descrevem as características e restrições do sistema, além de seu comportamento. Eles abrangem atributos de qualidade como desempenho, segurança, usabilidade, confiabilidade, entre outros. Exemplo: "O sistema de uma instituição financeira deve ter uma resposta de tempo inferior a 2 segundos para todas as transações financeiras" ou "O sistema deve ser compatível com os navegadores Chrome, Firefox e Safari". <br/>

DESAFIO- Escreva 2 exemplos de trade-offs envolvendo requisitos não funcionais. <br/>

1- Desempenho versus Custos: Um exemplo de trade-off entre requisitos não funcionais é o equilíbrio entre o desempenho do sistema e os custos de desenvolvimento e manutenção. Investir em recursos de hardware mais avançados, como servidores mais poderosos, pode melhorar significativamente o desempenho do sistema, mas isso também implica em custos mais altos. Portanto, deve-se considerar cuidadosamente o custo-benefício de investir em melhorias de desempenho em relação ao orçamento disponível.

2- Usabilidade versus Segurança: Outro exemplo de trade-off ocorre entre a usabilidade e a segurança do sistema. Aumentar a segurança geralmente envolve a implementação de medidas adicionais, como autenticação de vários fatores e requisitos de senha complexos. No entanto, essas medidas podem tornar o sistema mais complexo e difícil de usar para os usuários finais. Portanto, é necessário encontrar um equilíbrio entre fornecer uma experiência de usuário intuitiva e garantir um nível adequado de segurança para proteger os dados e informações do sistema.

Aula 4- 24/03/23

Classe UML

![Diagrama em branco - Classe UML (1)](https://github.com/Hugohs98/bertoti/assets/111614142/16cb7a80-b39e-498c-b01d-806ca19d5069)

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
