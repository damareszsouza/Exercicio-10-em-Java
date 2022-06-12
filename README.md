# Exercicio-10-em-Java
# Exercicio replicado do livro Tutorial de Programação em Java e Orientação a Objetos


//Classe ponto
class Ponto {
public float x,y;
public Ponto(float ax,float ay) { //omita o valor de retorno! garante o estado do objeto
 this.x = ax; this.y = ay;
}
public void move(float dx,float dy) {
 this.x += dx; this.y += dy;
}
public String toString() {
 return "(" + this.x + "," + this.y + ")"; //(x,y)
}
}
//Classe principal, Arquivo Principal.java
class Principal {

public static void main(String args[]) {
//preparacao das variaveis copia de objetos
 Ponto pOriginal, pAlias, pCopia;
 pOriginal = new Ponto((float)0.0,0.0f); //(float)0.0 ou 0.0f; 0.0 eh double
 pAlias = pOriginal; //copiando atraves de atribuica
 pCopia = new Ponto(pOriginal.x, pOriginal.y); //copiando atributo por atributo 
//resultados
 System.out.println("Original:" + pOriginal);
 System.out.println("Alias:" + pOriginal);
 System.out.println("Modificando Alias.x para 2");
 pAlias.x = 2.0f;
 System.out.println("Veja como o original ficou:" + pOriginal);
 System.out.println("pCopia nao se modifica:" + pCopia);
//comparacao de objetos
 System.out.println("Original==Alias:" + (pOriginal == pAlias) );
 System.out.println("Copia==Original:" + (pCopia == pOriginal) );
 System.out.println("Deixando atributos de Copia iguais aos de Original");
 pCopia.x = 2;
 System.out.println("Copia==Original:" + (pCopia == pOriginal) );
 System.out.println("Original.x==Copia.x:" + (pCopia.x == pOriginal.x) );
 System.out.println("Original.y==Copia.y:" + (pCopia.y == pOriginal.y) );
 
 //COMENTARIOS
//preparacao das variaveis, copia de objetos:
pAlias e uma referência para o mesmo local de memória que pOriginal, por este motivo
quando pAlias é alterado, pOriginal se altera por “efeito colateral”, eles compartilham o mesmo
objeto pois a atribuição pAlias = pOriginal, copia o endereço de pOriginal.
Já pCopia, é o resultado de uma nova alocação de memória, portanto um novo endereço, um
objeto independente dos outros. 
//comparacao de objetos:
pOriginal == pAlias e outras comparações equivalentes têm o significado de comparação do
endereço de memória e não do conteúdo.
pOriginal.x == pCopia.x tem o significado de comparação do valor desses atributos, assim
como uma comparação entre inteiros. Se esses atributos por sua vez fossem objetos (tipo Integer ao
envés de int), esta operação teria o significado de comparação entre endereços de memória dos
objetos.
As possíveis soluções, comentadas incluindo verificação da classe dos objetos
//Classe Ponto
class Ponto {
public float x,y;
public Ponto(float ax,float ay) { //omita o valor de retorno!
//garante o estado do objeto
this.x = ax; this.y = ay;
}
public void move(float dx,float dy) {
this.x += dx; this.y += dy;
}
public String toString() {
return "(" + this.x + "," + this.y + ")"; //(x,y)
}
public boolean equals(Ponto outro) { //equals significa igual
return ((outro.x == this.x) && (outro.y == this.y)); //this==outro?
}
 
 public void copy(Ponto outro) {
 this.x = outro.x;
 this.y = outro.y;
 }
 public Ponto clone() {
 Ponto cloned = new Ponto(this.x, this.y);
 return cloned;
 }
} 

//preparacao das variaveis
 Ponto pOriginal, pCopia1, pCopia2;
 pOriginal = new Ponto((float)0.0,0.0f); //(float)0.0 ou 0.0f; 0.0 eh double
 pCopia1 = new Ponto(0.0f,0.0f);
 pCopia1.copy(pOriginal); //pCopia1 copia conteudo de pOriginal nele mesmo
 pCopia2 = (Ponto) pOriginal.clone();
//copia de objetos
 System.out.println("Original:" + pOriginal);
 System.out.println("Copia1:" + pCopia1);
 System.out.println("Copia2:"+pCopia2);
 System.out.println("Modificando Copia1.x para 2");
 pCopia1.x=2.0f;
 System.out.println("Veja como o original ficou:"+pOriginal);
 System.out.println("Copia2 nao se modifica:"+pCopia2);
//comparacao de objetos
 System.out.println("Original==Copia2:"+(pOriginal==pCopia2) );
 System.out.println("Original.igual(Copia2):" + pOriginal.equals(pCopia2) );
 System.out.println("Deixando atributos de Copia iguais aos de Original");
 
//verificacao da classe dos objetos
 System.out.println("Obtendo a classe dos objetos");
 System.out.println(pOriginal.getClass().getName());
 System.out.print("Original e da classe Ponto?");
 boolean result = (pOriginal instanceof Ponto);
 System.out.println(result);
 }
}

//Classe principal, Arquivo Principal.java
class Principal {
public static void main(String args[]) {
