# semaforos-cidades-inteligentes-package campinas;
/*  Em dupla, escolha um dos cenários abaixo e implemente parte do sistema em Java
    utilizando os conceitos da orientação objeto. A implementação deve conter no 
    mínimo: quatro classes(sendo uma abstrata), duas relações de herança e uma interface. 
    A implementação também deve conter uma classe executável parateste. Além da 
    implementação em Java, a dupla também deveentregar os diagramas de classe UML
    da solução apresentada. 
*/

//Cenário15: Semáforos Controle automático de diversos semáforos em uma cidade inteligente. 

public class Expressa extends Controlador implements Demanda{
    private String aproximacao; 
    private int temporizador;
    private String EstagioCor;
    
    public Expressa(String aproximacao) {
        this.aproximacao = aproximacao;
        System.out.println("Cruzamento: " + this.aproximacao 
                           +"\nExpressa Cor: " + this.getCor());
        
        for(temporizador=4; temporizador>0; temporizador--){
            System.out.println("Tempo: " + this.temporizador);
        }
        setCor("Verde");
        System.out.println("Cruzamento: " + this.aproximacao 
                           +"\nExpressa Cor: " + this.getCor() + "\n");
    }

    public String getAproximacao() {
        return aproximacao;
    }

    public void setAproximacao(String aproximacao) {
        this.aproximacao = aproximacao;
    }
    
    public void setEstagioCor(String EstagioCor) {
        this.EstagioCor = EstagioCor;
        //this.setCor(EstagioCor);
        this.setCor(EstagioCor);
    }
    
    @Override
    public void mostrarCruzamento(){
        System.out.println("Avenida: " + this.getRua()
                           + "\nAproximação: " + this.aproximacao
                           + "\nCor: " + this.getCor());        
    }
    
    public void setDemanda() {
    
    }
    
    
}


package campinas;

import java.util.Scanner;

public class Transversal extends Controlador implements Demanda {
    Scanner Demanda = new Scanner(System.in);

    public Transversal() {
         System.out.println("Transversal" + " Cor: " + this.getCor()+ "\n");
    }
    
    @Override
    public void setDemanda() {
        System.out.println("H");
        Expressa Demanda1 = new Expressa("Demanda Retorno Shopping");
        Demanda1.setEstagioCor("Amarelo");
        System.out.println("Expressa Cor: " + Demanda1.getCor());
        Demanda1.setEstagioCor("Vermlho");
        System.out.println("Expressa Cor: " + Demanda1.getCor());
        
        setCor("Verde");       
    }
       
    @Override
    public void mostrarCruzamento(){
        System.out.println("Rua: " + this.getRua()
                           + "\nCor: " + this.getCor());    
   }   
}


package campinas;

public class Semaforica {

    public static void main(String[] args) {
        Expressa JBD = new Expressa("Retorno Shopping");
        Transversal Shop = new Transversal();
        Shop.setDemanda();
       JBD.mostrarCruzamento();
    }
    
}
