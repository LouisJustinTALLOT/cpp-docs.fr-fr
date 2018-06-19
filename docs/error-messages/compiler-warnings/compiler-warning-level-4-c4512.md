---
title: Compilateur avertissement (niveau 4) C4512 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4512
dev_langs:
- C++
helpviewer_keywords:
- C4512
ms.assetid: afb68995-684a-4be5-a73a-38d7a16dc030
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d87a79fcdc4c1ac79b1237032f6cfb5a52b9e269
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293915"
---
# <a name="compiler-warning-level-4-c4512"></a>Avertissement du compilateur (niveau 4) C4512
'classe' : l'opérateur d'assignation n'a pas pu être généré.  
  
 Le compilateur ne peut pas générer un opérateur d'assignation pour la classe donnée. Aucun opérateur d'assignation n'a été créé.  
  
 Un opérateur d'assignation pour la classe de base qui n'est pas accessible à la classe dérivée peut provoquer cet avertissement.  
  
 Pour éviter cet avertissement, spécifiez pour la classe un opérateur d'assignation défini par l'utilisateur.  
  
 Le compilateur générera aussi une fonction d'opérateur d'assignation pour une classe qui n'en définit pas. Cet opérateur d'assignation est une copie membre des données membres d'un objet. Comme les éléments de données `const` ne peuvent pas être modifiés après l'initialisation, si la classe contient un élément `const`, l'opérateur d'assignation par défaut ne fonctionne pas. L'avertissement C4512 peut aussi être lié à une déclaration de données membres non statiques de type référence. Si votre intention est de créer un type non reproductible, vous devez aussi empêcher la création d'un constructeur de copie par défaut.  
  
 Vous pouvez résoudre l'avertissement C4512 pour votre code de trois manières différentes :  
  
-   Définissez explicitement un opérateur d'assignation pour la classe.  
  
-   Supprimer **const** ou l’opérateur de référence de l’élément de données dans la classe.  
  
-   Utiliser le #pragma [avertissement](../../preprocessor/warning.md) instruction pour supprimer l’avertissement.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant génère l'erreur C4512.  
  
```  
// C4512.cpp  
// compile with: /EHsc /W4  
// processor: x86  
  
class Base {  
private:  
   const int a;  
  
public:  
   Base(int val = 0) : a(val) {}  
   int get_a() { return a; }  
};   // C4512 warning  
  
class Base2 {  
private:  
   const int a;  
  
public:  
   Base2(int val = 0) : a(val) {}  
   Base2 & operator=( const Base2 & ) { return *this; }  
   int get_a() { return a; }  
};  
  
// Type designer intends this to be non-copyable because it has a   
// reference member  
class Base3  
{  
private:  
   char& cr;  
  
public:  
   Base3(char& r) : cr(r) {}  
   // Uncomment the following line to explicitly disable copying:  
   // Base3(const Base3&) = delete;   
};   // C4512 warning  
  
int main() {  
   Base first;  
   Base second;  
  
   // OK  
   Base2 first2;  
   Base2 second2;  
  
   char c = 'x';  
   Base3 first3(c);  
   Base3 second3 = first3; // C2280 if no default copy ctor  
}  
```