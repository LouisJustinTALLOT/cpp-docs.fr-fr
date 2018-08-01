---
title: Littéraux numériques, booléen et pointeur (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- literals, C++
- constants, literals
- literals [C++]
ms.assetid: 17c09fc3-3ad7-47e2-8b48-ba8ae994edc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a445e9c435f9e077899a2a473dc5862f98a36bf4
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405517"
---
# <a name="numeric-boolean-and-pointer-literals--c"></a>Littéraux numériques, booléen et pointeur (C++)
Un littéral est un élément de programme qui représente directement une valeur. Cet article traite des littéraux de type entier, virgule flottante, booléen et de pointeur. Pour plus d’informations sur les littéraux de chaîne et de caractère, consultez [chaîne et les littéraux de caractère (C++)](../cpp/string-and-character-literals-cpp.md). Vous pouvez également définir vos propres littéraux basés sur un de ces catégories. Pour plus d’informations, consultez [littéraux définis par l’utilisateur (C++)](../cpp/user-defined-literals-cpp.md)  
  
 . Vous pouvez utiliser des littéraux dans de nombreux contextes, mais le plus souvent pour initialiser des variables nommées et passer des arguments à des fonctions :  
  
```cpp 
const int answer = 42; // integer literal  
double d = sin(108.87);     //floating point literal passed to sin function  
bool b = true;              // boolean literal  
MyClass* mc = nullptr;      // pointer literal  
```  
  
 Parfois, il est important indiquer au compilateur comment interpréter un littéral ou le type spécifique à lui affecter. Pour cela, ajoutez des préfixes ou suffixes au littéral. Par exemple, le préfixe 0x indique au compilateur d'interpréter le nombre qui le suit en tant que valeur hexadécimale, par exemple 0x35. Le suffixe ULL indique au compilateur de traiter la valeur un **unsigned long long** type, comme dans 5894345ULL. Consultez les sections suivantes pour obtenir la liste complète des préfixes et suffixes pour chaque type de littéral.  
  
## <a name="syntax"></a>Syntaxe  
  
## <a name="integer-literals"></a>Littéraux d'entier  
 Les littéraux d'entier commencent par un chiffre et n'ont aucune partie fractionnaire ni exposant. Vous pouvez spécifier les littéraux d'entier sous forme décimale, octale ou hexadécimale. Ils peuvent spécifier des types signés ou non signés, longs ou courts.  
  
 Si aucun préfixe ou suffixe n’est spécifiée, le compilateur génère un type de valeur littérale intégral **int** (32 bits), si la valeur ne tient pas, dans le cas contraire, il génère un type **longue** (64 bits).  
  
 Pour spécifier un littéral intégral décimal, commencez la spécification par un chiffre différent de zéro. Exemple :  
  
```cpp 
int i = 157;   // Decimal literal  
int j = 0198;       // Not a decimal number; erroneous octal literal  
int k = 0365;       // Leading zero specifies octal literal, not decimal  
int m = 36'000'000  // digit separators make large values more readable  
int   
```  
  
 Pour spécifier un littéral intégral octal, commencez la spécification par 0, suivi d'une séquence de chiffres dans la plage 0 à 7. Les chiffres 8 et 9 sont des erreurs lors de la spécification d'un littéral octal. Exemple :  
  
```cpp 
int i = 0377;   // Octal literal  
int j = 0397;        // Error: 9 is not an octal digit  
```  
  
 Pour spécifier un littéral intégral hexadécimal, commencez la spécification par `0x` ou `0X` (la casse de « x » n'a pas d'importance) suivi d'une séquence de chiffres dans la plage `0` à `9` et `a` (ou `A`) à `f` (ou `F`). Les chiffres hexadécimaux `a` (ou `A`) à `f` (ou `F`) représentent des valeurs dans la plage 10 à 15. Exemple :  
  
```cpp 
int i = 0x3fff;   // Hexadecimal literal  
int j = 0X3FFF;        // Equal to i  
```  
  
 Pour spécifier un type non signé, utilisez le `u` ou `U` suffixe. Pour spécifier un type long, utilisez le `l` ou `L` suffixe. Pour spécifier un type intégral 64 bits, utilisez le suffixe LL ou ll. Le suffixe i64 est toujours pris en charge mais doit être évité, car il est spécifique à Microsoft et n'est pas portable. Exemple :  
  
```cpp 
unsigned val_1 = 328u;             // Unsigned value  
long val_2 = 0x7FFFFFL;                 // Long value specified   
                                        //  as hex literal  
unsigned long val_3 = 0776745ul;        // Unsigned long value  
auto val_4 = 108LL;                           // signed long long  
auto val_4 = 0x8000000000000000ULL << 16;     // unsigned long long   
```  
  
 **Séparateurs de chiffres**: vous pouvez utiliser le caractère guillemet unique (apostrophe) pour séparer les valeurs d’emplacement dans un nombre plus important pour les rendre plus facile à lire. Les séparateurs n'ont pas d'effet sur la compilation.  
  
```cpp 
long long i = 24'847'458'121  
```  
  
## <a name="floating-point-literals"></a>Littéraux à virgule flottante  
 Les littéraux à virgule flottante spécifient des valeurs qui doivent avoir une partie fractionnaire. Ces valeurs contiennent des virgules décimales (**.**) et peuvent contenir des exposants.  
  
 Les littéraux à virgule flottante ont une « mantisse », qui spécifie la valeur du nombre, un « exposant, » qui spécifie la grandeur du nombre, et un suffixe facultatif qui spécifie le type du littéral. La mantisse est spécifiée comme une séquence de chiffres suivis d'un point, suivie d'une séquence facultative de chiffres représentant la partie fractionnaire du nombre. Par exemple :  
  
```cpp 
18.46  
38.  
```  
  
 L'exposant, s'il est présent, spécifie la grandeur du nombre comme puissance de 10, comme indiqué dans l'exemple suivant :  
  
```cpp 
18.46e0      // 18.46  
18.46e1           // 184.6  
```  
  
 L’exposant peut être spécifié à l’aide de `e` ou `E`, qui ont la même signification, suivie d’un signe facultatif (+ ou -) et une séquence de chiffres.  Si un exposant est présent, la virgule décimale de fin est inutile dans les nombres entiers tels que `18E0`.  
  
 Par défaut des littéraux à virgule flottante en type **double**. Grâce aux suffixes `f` ou `l` (ou `F` ou `L` — le suffixe n’est pas sensible à la casse), le littéral peut être spécifié en tant que **float** ou **double long**, respectivement.  
  
 Bien que **long double** et **double** ont la même représentation, elles ne sont pas du même type. Par exemple, vous pouvez avoir des fonctions surchargées comme  
  
```cpp 
void func( double );  
```  
  
 et  
  
```cpp 
void func( long double );  
```  
  
## <a name="boolean-literals"></a>Littéraux booléens  
 Les littéraux booléens sont **true** et **false**.  
  
## <a name="pointer-literal-c11"></a>Littéral de pointeur (C++11)  
 C++ introduit la [nullptr](../cpp/nullptr.md) littéral pour spécifier un pointeur initialisé à zéro. Dans le code portable, **nullptr** doit être utilisé au lieu de zéro de type intégral ou macros comme NULL.  
  
## <a name="binary-literals-c14"></a>Littéraux binaires (C++14)  
 Un littéral binaire peut être spécifié à l'aide du préfixe `0B` ou `0b`, suivi d'une séquence de 1 et de 0 :  
  
```cpp 
auto x = 0B001101 ; // int  
auto y = 0b000001 ; // int  
```  
  
## <a name="avoid-using-literals-as-magic-constants"></a>Évitez d'utiliser des littéraux en tant que « constantes magiques »  
 Vous pouvez utiliser des littéraux directement dans les expressions et instructions bien qu'il ne s'agisse pas toujours d'une bonne pratique de programmation :  
  
```cpp 
if (num < 100)  
    return "Success";  
```  
  
 Dans l'exemple précédent, il peut être préférable d'utiliser une constante nommée avec une signification claire, par exemple « MAXIMUM_ERROR_THRESHOLD ». De plus, si la valeur de retour « Opération réussie » est visible par les utilisateurs finaux, il peut être préférable d'utiliser une constante de chaîne nommée qui peut être stockée à un emplacement unique dans un fichier d'où elle peut être localisée dans d'autres langues. L'utilisation de constantes nommées permet à d'autres utilisateurs ainsi qu'à vous-même de comprendre l'objectif du code.  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions lexicales](../cpp/lexical-conventions.md)   
 [Littéraux de chaîne C++](../cpp/string-and-character-literals-cpp.md)   
 [Littéraux C++ définis par l’utilisateur](../cpp/user-defined-literals-cpp.md)