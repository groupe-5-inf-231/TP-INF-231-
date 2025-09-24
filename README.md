# TP-INF-231-
/*
==================================================
RAPPORT : Multiplication par addition en C
==================================================

1. Objectif :
   Implémenter une fonction qui calcule le produit 
   de deux entiers positifs a et b sans utiliser 
   l’opérateur de multiplication (*).

2. Méthode :
   - On ajoute le nombre 'a' à lui-même 'b' fois.
   - Exemple : 5 × 3 = 5 + 5 + 5 = 15.

3. Organisation :
   Ici, tout le code est regroupé dans un seul fichier 
   pour simplifier la compilation et l’exécution.
   On définit :
   - une fonction mult_addition()
   - un main() pour tester le programme.

4. Compilation :
   gcc programme.c -o prog

5. Exécution :
   ./prog

6. Résultat attendu :
   Exemple : a = 7, b = 4
   Affiche : 7 × 4 = 28

==================================================
*/

#include <stdio.h>

// Fonction qui effectue la multiplication par addition
int mult_addition(int a, int b) {
    int resultat = 0;
    for (int i = 0; i < b; i++) {
        resultat += a;  // On ajoute 'a', b fois
    }
    return resultat;
}

// Fonction principale pour tester
int main() {
    int a = 7, b = 4;
    printf("%d × %d = %d\n", a, b, mult_addition(a, b));
    return 0;
}
