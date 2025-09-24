NOMS ET MATRICULES DES PARTICIPANTS:
-BEYALA OMBE EVRARD MARIE FRANCKY 23V2527
-YOUMBI KEMKENG ANGE CHLOE  24G2434
-HAPI LAYOU MARTIAL  23V2206
-SEBDOU EMMANUEL  23U2723
-ARIEGNIGNI KHADYE KHAIRA  24G2619
-TATAH FOTOUO TCHOFFO HENDERLAIN  24G2864


# TP-INF-231-
/*
==================================================
EXERCICE 1 : Somme de matrices
==================================================
Objectif : Additionner deux matrices de même taille.
Méthode : On additionne élément par élément.
*/

#include <stdio.h>

// Somme de matrices
void somme_matrices(int A[3][3], int B[3][3], int C[3][3]) {
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            C[i][j] = A[i][j] + B[i][j];
        }
    }
}

/*
==================================================
EXERCICE 2 : Produit de matrices
==================================================
Objectif : Multiplier deux matrices.
Méthode : C[i][j] = somme(A[i][k] * B[k][j]).
*/

void produit_matrices(int A[3][3], int B[3][3], int C[3][3]) {
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            C[i][j] = 0;
            for (int k = 0; k < 3; k++) {
                C[i][j] += A[i][k] * B[k][j];
            }
        }
    }
}

/*
==================================================
EXERCICE 3 : Recherche séquentielle
==================================================
Objectif : Chercher un élément dans un tableau.
Méthode : On parcourt le tableau jusqu’à trouver la valeur.
*/

int recherche_seq(int tab[], int n, int val) {
    for (int i = 0; i < n; i++) {
        if (tab[i] == val) {
            return i;
        }
    }
    return -1;
}

/*
==================================================
EXERCICE 4 : Multiplication a × b par addition
==================================================
Objectif : Calculer a × b sans l’opérateur *.
Méthode : Ajouter a, b fois.
*/

int mult_addition(int a, int b) {
    int resultat = 0;
    for (int i = 0; i < b; i++) {
        resultat += a;
    }
    return resultat;
}

/*
==================================================
EXERCICE 5 : Tester si un tableau est trié
==================================================
Objectif : Vérifier l’ordre croissant.
Méthode : Comparer tab[i] et tab[i+1].
*/

int estTrie(int tab[], int n) {
    for (int i = 0; i < n - 1; i++) {
        if (tab[i] > tab[i + 1]) {
            return 0;
        }
    }
    return 1;
}

/*
==================================================
EXERCICE 6 : Médiane dans un tableau
==================================================
Objectif : Trouver la médiane (élément du milieu).
Méthode : Trier le tableau puis prendre l’élément du centre.
*/

void trier(int tab[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = i + 1; j < n; j++) {
            if (tab[i] > tab[j]) {
                int temp = tab[i];
                tab[i] = tab[j];
                tab[j] = temp;
            }
        }
    }
}

int mediane(int tab[], int n) {
    trier(tab, n);
    if (n % 2 == 1) {
        return tab[n / 2];
    } else {
        return (tab[n/2 - 1] + tab[n/2]) / 2;
    }
}

/*
==================================================
EXERCICE 7 : Inverser un tableau
==================================================
Objectif : Inverser l’ordre des éléments.
Méthode : Échanger le premier avec le dernier, etc.
*/

void inverse_tableau(int tab[], int n) {
    for (int i = 0; i < n / 2; i++) {
        int temp = tab[i];
        tab[i] = tab[n - 1 - i];
        tab[n - 1 - i] = temp;
    }
}

/*
==================================================
EXERCICE 8 : Produit vectoriel
==================================================
Objectif : Calculer le produit vectoriel de deux vecteurs 3D.
Méthode : Déterminant classique.
*/

void produit_vectoriel(int u[3], int v[3], int w[3]) {
    w[0] = u[1]*v[2] - u[2]*v[1];
    w[1] = u[2]*v[0] - u[0]*v[2];
    w[2] = u[0]*v[1] - u[1]*v[0];
}

/*
==================================================
EXERCICE 9 : Produit vecteur × matrice
==================================================
Objectif : Multiplier un vecteur ligne par une matrice.
Méthode : w[j] = somme(v[i] * M[i][j]).
*/

void produit_vecteur_matrice(int v[3], int M[3][3], int w[3]) {
    for (int j = 0; j < 3; j++) {
        w[j] = 0;
        for (int i = 0; i < 3; i++) {
            w[j] += v[i] * M[i][j];
        }
    }
}

/*
==================================================
MAIN : Tests de toutes les fonctions
==================================================
*/

int main() {
    // Test Exercice 1 et 2 : matrices
    int A[3][3] = {{1,2,3},{4,5,6},{7,8,9}};
    int B[3][3] = {{9,8,7},{6,5,4},{3,2,1}};
    int C[3][3];
    
    somme_matrices(A, B, C);
    printf("Somme de matrices :\n");
    for (int i=0;i<3;i++){for(int j=0;j<3;j++) printf("%d ",C[i][j]); printf("\n");}

    produit_matrices(A, B, C);
    printf("Produit de matrices :\n");
    for (int i=0;i<3;i++){for(int j=0;j<3;j++) printf("%d ",C[i][j]); printf("\n");}

    // Test Exercice 3 : recherche
    int tab[] = {1,4,7,9,12};
    int pos = recherche_seq(tab, 5, 9);
    printf("Recherche séquentielle (9 trouvé à la position) : %d\n", pos);

    // Test Exercice 4 : multiplication par addition
    printf("7 × 4 = %d\n", mult_addition(7,4));

    // Test Exercice 5 : tableau trié
    int tab2[] = {1,2,3,4,5};
    int tab3[] = {5,3,2,1};
    printf("Tab2 trié ? %d\n", estTrie(tab2,5));
    printf("Tab3 trié ? %d\n", estTrie(tab3,4));

    // Test Exercice 6 : médiane
    int tab4[] = {7,1,5,3,9};
    printf("Médiane = %d\n", mediane(tab4,5));

    // Test Exercice 7 : inversion
    int tab5[] = {1,2,3,4,5};
    inverse_tableau(tab5,5);
    printf("Tab5 inversé : ");
    for(int i=0;i<5;i++) printf("%d ", tab5[i]); printf("\n");

    // Test Exercice 8 : produit vectoriel
    int u[3]={1,2,3}, v[3]={4,5,6}, w[3];
    produit_vectoriel(u,v,w);
    printf("Produit vectoriel : (%d,%d,%d)\n",w[0],w[1],w[2]);

    // Test Exercice 9 : vecteur × matrice
    int vec[3]={1,2,3}, res[3];
    produit_vecteur_matrice(vec,A,res);
    printf("Vecteur × matrice : (%d,%d,%d)\n",res[0],res[1],res[2]);

    return 0;
}


METHODES POUR COMPILER ET EXECUTER:
    il faut saisir les commandes ci apres:
           -gcc programme.c -o prog
           -./prog
     
        
