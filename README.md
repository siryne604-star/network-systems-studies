package ex3tP4;

public class Comptabilite {
	 private Compte[] listeComptes;
	 private int nbComptesExistans;
	 private final int nbMaxComptes=1000;
	 

	 public Comptabilite() {
	        this.listeComptes = new Compte[this.nbMaxComptes];
	        this.nbComptesExistans = 0;
	    }
	 //ajouter dans la premier  case vide!
	 public void ajouterCompte(Compte c) {
		    if (nbComptesExistans < nbMaxComptes) {
		        listeComptes[nbComptesExistans] = c;
		        nbComptesExistans = nbComptesExistans + 1;
		    } else {
		        System.out.println("Erreur, capacité maximale atteinte");
		    }
	}
	  public void afficherComptes(){
	        for (int i = 0; i < nbComptesExistans; i++) 
	        	if(listeComptes[i]!=null)
	            listeComptes[i].afficher();
	        
	  }
	  public void desactiverCompte(int code) {
	        for (int i = 0; i < nbComptesExistans; i++) {
	            if (listeComptes[i].getCode()== code) {
	                listeComptes[i].setEtat(false); 
	                System.out.println("Le compte Num" + code + "est désactivé.");
	                return;
	            }
	        }
	        System.out.println("Erreur : Compte introuvable ");
	  }
	  public void supprimerCompte(int code) {
	        int index = -1;
	        for (int i = 0; i < nbComptesExistans; i++) {
	            if (listeComptes[i].getCode() == code) {
	                index = i;
	                break;
	            }
	        }

	        if (index == -1) {
	            System.out.println("Erreur : Compte introuvable pour la suppression.");
	            return;
	        }
	        for (int i = index; i < nbComptesExistans - 1; i++) {
	            listeComptes[i] = listeComptes[i + 1];
	        }
	        listeComptes[nbComptesExistans - 1] = null; 
	        nbComptesExistans = nbComptesExistans - 1;  
	        System.out.println("Le compte Num" + code + "est supprimé.");
	    }
	  public void afficherTotalSoldes() {
	        double total = 0;
	        for (int i = 0; i < nbComptesExistans; i++) {
	        	if(listeComptes[i]!=null)
	            total = total + listeComptes[i].getSolde(); 
	        }
	        System.out.println("Total des soldes de la comptabilité : " + total + " DT");
	    }
	  
	  
	  
}
