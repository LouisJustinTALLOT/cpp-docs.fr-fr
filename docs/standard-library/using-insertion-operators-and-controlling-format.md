---
title: "Utilisation des opérateurs d’insertion et contrôle du format | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- insertion operators
ms.assetid: cdefe986-6548-4cd1-8a67-b431d7d36a1c
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 96d388b7ddfdf561e016b4e74ffeb9ca072c7cb2
ms.contentlocale: fr-fr
ms.lasthandoff: 04/29/2017

---
# <a name="using-insertion-operators-and-controlling-format"></a>Utilisation des opérateurs d'insertion et contrôle du format
Cette rubrique montre comment contrôler le format et comment créer des opérateurs d'insertion pour vos propres classes. L’opérateur d’insertion (**<<**), qui préprogrammé pour tous les types de données C++ standard, envoie des octets à un objet de flux de sortie. Les opérateurs d’insertion fonctionnent avec des « manipulateurs » prédéfinis, qui sont des éléments qui modifient le format par défaut des arguments de type entier.  
  
 Vous pouvez contrôler le format avec les options suivantes :  
  
- [Largeur de sortie](#vclrfoutputwidthanchor3)  
  
- [Alignement](#vclrfalignmentanchor4)  
  
- [Précision](#vclrfprecisionanchor5)  
  
- [Base](#vclrfradixanchor6)  
  
##  <a name="vclrfoutputwidthanchor3"></a> Largeur de sortie  
 Pour aligner la sortie, vous spécifiez la largeur de sortie pour chaque élément en plaçant le manipulateur `setw` dans le flux ou en appelant la fonction membre **width**. Cet exemple aligne à droite les valeurs dans une colonne d'au moins 10 caractères de large :  
  
```  
// output_width.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };  
   for( int i = 0; i < 4; i++ )  
   {  
      cout.width(10);  
      cout << values[i] << '\n';  
   }  
}  
```  
  
### <a name="output"></a>Sortie  
  
```  
    1.23 
    35.36 
    653.7 
4358.24  
```  
  
 Des espaces de début sont ajoutés à toute valeur dont la largeur est inférieure à 10 caractères.  
  
 Pour remplir un champ, utilisez la fonction membre **fill**, qui définit la valeur du caractère de remplissage pour les champs qui ont une largeur spécifiée. La valeur par défaut est un espace. Pour remplir la colonne de nombres avec des astérisques, modifiez la boucle **for** précédente comme suit :  
  
```  
for(int i = 0; i <4; i++)  
{  
    cout.width(10);

 cout.fill('*');

    cout <<values[i] <<endl;  
}  
```  
  
 Le manipulateur `endl` remplace le caractère de saut de ligne (`'\n'`). La sortie ressemble à ceci :  
  
```  
******1.23  
*****35.36  
*****653.7  
***4358.24  
```  
  
 Pour spécifier les largeurs des éléments de données sur la même ligne, utilisez le manipulateur `setw` :  
  
```  
// setw.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iomanip>  
using namespace std;  
  
int main( )  
{  
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };  
   char *names[] = { "Zoot", "Jimmy", "Al", "Stan" };  
   for( int i = 0; i < 4; i++ )  
      cout << setw( 6 )  << names[i]  
           << setw( 10 ) << values[i] << endl;  
}  
```  
  
### <a name="output"></a>Sortie  
 La fonction membre **width** est déclarée dans \<iostream>. Si vous utilisez `setw` ou tout autre manipulateur avec des arguments, vous devez inclure \<iomanip>. Dans la sortie, les chaînes sont imprimées dans un champ de largeur 6 et les entiers dans un champ de largeur 10 :  
  
```  
    Zoot 1.23  
Jimmy     35.36  
    Al 653.7  
    Stan 4358.24  
```  
  
 Ni `setw` ni **width** ne tronquent les valeurs. Si la sortie mise en forme dépasse la largeur, la valeur entière est imprimée, conformément au paramètre de précision du flux. `setw` et **width** affectent tous deux uniquement le champ suivant. La largeur de champ reprend son comportement par défaut (la largeur nécessaire) une fois qu'un champ a été imprimé. Toutefois, les autres options de format de flux restent en vigueur jusqu'à ce qu'elles soient modifiées.  
  
##  <a name="vclrfalignmentanchor4"></a> Alignement  
 Les flux de sortie sont par défaut alignés à droite. Pour aligner à gauche les noms dans l’exemple précédent et aligner à droite les nombres, remplacez la boucle **for** comme suit :  
  
```  
for (int i = 0; i <4; i++)  
    cout <<setiosflags(ios::left)  
 <<setw(6)  <<names[i]  
 <<resetiosflags(ios::left)  
 <<setw(10) <<values[i] <<endl;  
```  
  
 La sortie ressemble à ceci :  
  
```  
Zoot        1.23  
Jimmy      35.36  
Al         653.7  
Stan     4358.24  
```  
  
 L’indicateur d’alignement à gauche est défini à l’aide du manipulateur [setiosflags](../standard-library/iomanip-functions.md#setiosflags) avec l’énumérateur `left`. Cet énumérateur est défini dans la classe [ios](../standard-library/basic-ios-class.md). Sa référence doit donc inclure le préfixe **ios::**. Le manipulateur [resetiosflags](../standard-library/iomanip-functions.md#resetiosflags) désactive l’indicateur d’alignement à gauche. Contrairement à **width** et `setw`, l’effet de `setiosflags` et `resetiosflags` est permanent.  
  
##  <a name="vclrfprecisionanchor5"></a> Précision  
 La valeur par défaut pour la précision de virgule flottante est six. Par exemple, le nombre 3466,9768 est imprimé comme 3466,98. Pour modifier comment cette valeur est imprimée, utilisez le manipulateur [setprecision](../standard-library/iomanip-functions.md#setprecision). Le manipulateur a deux indicateurs : [fixed](../standard-library/ios-functions.md#fixed) et [scientific](../standard-library/ios-functions.md#scientific). Si [fixed](../standard-library/ios-functions.md#fixed) est défini, le nombre imprimé est 3466,976800. Si **scientific** est défini, le nombre imprimé est 3,4669773+003.  
  
 Pour afficher les nombres à virgule flottante illustrés dans [Alignement](#vclrfalignmentanchor4) avec un chiffre significatif, remplacez la boucle **for** comme suit :  
  
```  
for (int i = 0; i <4; i++)  
    cout <<setiosflags(ios::left)  
 <<setw(6)    
 <<names[i]  
 <<resetiosflags(ios::left)  
 <<setw(10)   
 <<setprecision(1)  
 <<values[i]   
 <<endl;  
```  
  
 Le programme imprime cette liste :  
  
```  
Zoot          1  
Jimmy     4e+001  
Al        7e+002  
Stan      4e+003  
```  
  
 Pour éliminer la notation scientifique, insérez cette instruction avant la boucle **for** :  
  
```  
cout <<setiosflags(ios::fixed);
```  
  
 Avec la notation fixe, le programme imprime un chiffre après la virgule décimale.  
  
```  
Zoot         1.2  
Jimmy       35.4  
Al         653.7  
Stan      4358.2  
```  
  
 Si vous remplacez l’indicateur **ios::fixed** par **ios::scientific**, le programme imprime :  
  
```  
Zoot    1.2e+000  
Jimmy   3.5e+001  
Al      6.5e+002  
Stan    4.4e+003  
```  
  
 Là encore, le programme imprime un chiffre après la virgule décimale. Si **ios::fixed** ou **ios::scientific** est défini, la valeur de précision détermine le nombre de chiffres après la virgule décimale. Si ni l'un ni l'autre n'est défini, la valeur de précision détermine le nombre total de chiffres significatifs. Le manipulateur `resetiosflags` efface ces indicateurs.  
  
##  <a name="vclrfradixanchor6"></a> Base  
 Les manipulateurs **dec**, **oct** et **hex** définissent la base par défaut pour l’entrée et la sortie. Par exemple, si vous insérez le manipulateur **hex** dans le flux de sortie, l’objet traduit correctement la représentation de données internes des entiers dans un format de sortie hexadécimal. Les nombres sont affichés avec les chiffres a à f en minuscules si l’indicateur [uppercase](../standard-library/ios-functions.md#uppercase) est clear (par défaut) ; sinon, ils sont affichés en majuscules. La base par défaut est **dec** (décimal).  
  
## <a name="quoted-strings-c14"></a>Chaînes entre guillemets (C++14)  
 Quand vous insérez une chaîne dans un flux, vous pouvez facilement récupérer la même chaîne en appelant la fonction membre stringstream::str(). Toutefois, si vous souhaitez utiliser l'opérateur d'extraction pour insérer le flux dans une nouvelle chaîne à un moment ultérieur, vous pouvez obtenir un résultat inattendu, car l'opérateur >> par défaut s'arrête quand il rencontre le premier espace blanc.  
  
```  
 
std::stringstream ss;  
std::string inserted = "This is a sentence.";  
std::string extracted;  
 
ss <<inserted;  
ss>> extracted;  
 
std::cout <<inserted;     //  This is a sentence.  
std::cout <<extracted;   //   This  
```  
  
 Ce problème peut être contourné manuellement, mais pour rendre l'aller-retour de chaîne plus pratique, C++14 ajoute le manipulateur de flux `std::quoted` dans `<iomanip>`. Lors de l'insertion, `quoted()` entoure la chaîne avec un séparateur (guillemet double " par défaut) et lors de l'extraction il manipule le flux pour extraire tous les caractères jusqu'au séparateur final. Les guillemets incorporés sont précédés d’un caractère d’échappement (\\\\ par défaut).  
  
 Les délimiteurs sont présents uniquement dans l’objet de flux. Ils ne sont pas présents dans la chaîne extraite, mais ils le sont dans la chaîne retournée par [basic_stringstream::str](../standard-library/basic-stringstream-class.md#str)().  
  
 Le comportement d'espace blanc des opérations d'insertion et d'extraction est indépendant de la façon dont la chaîne est représentée dans le code. L'opérateur quoted est donc utile que la chaîne d'entrée soit un littéral de chaîne brut ou une chaîne standard. La chaîne d'entrée, quel que soit son format, peut avoir des guillemets incorporés, des sauts de ligne, des tabulations, et ainsi de suite, qui seront tous conservés par le manipulateur quoted().  
  
 Pour plus d’informations et des exemples de code complets, consultez [quoted]--brokenlink--(../Topic/%3Cios%3E%20functions.md#quoted).  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de sortie](../standard-library/output-streams.md)   


