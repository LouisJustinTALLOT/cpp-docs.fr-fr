---
title: Compilateur avertissement (niveau 1) C4743 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4743
dev_langs: C++
helpviewer_keywords: C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 28ab5a9535184ea06ab9dd8f6e6203b98992e975
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4743"></a>Avertissement du compilateur (niveau 1) C4743
'*type*'a une taille différente '*file1*'et'*fichier2*' : *nombre* et *nombre* octets  
  
 Une variable externe référencée ou définie dans deux fichiers possède des types différents dans ces fichiers, et le compilateur a déterminé que la taille de la variable dans *file1* diffère de la taille de la variable dans *fichier2*.  
  
 Il est important cas lorsque cet avertissement peut être émis pour C++. Si vous déclarez les mêmes types portant le même nom dans deux fichiers différents, si ces déclarations contiennent des fonctions virtuelles, et si les déclarations ne sont pas identiques, le compilateur peut émettre l’avertissement C4744 pour les tables de la fonction virtuelle. L’avertissement se produit, car il existe deux tables de fonctions virtuelles de taille différente pour le même type, et l’éditeur de liens doit choisir un d’eux à incorporer dans le fichier exécutable.  Il est possible que cela peut entraîner votre programme appelle la fonction virtuelle incorrecte.  
  
 Pour résoudre cet avertissement, utilisez la même définition de type ou utiliser des noms différents pour les types ou les variables.  
  
## <a name="example"></a>Exemple  
 Cet exemple contient une définition du type.  
  
```  
// C4743a.cpp  
// compile with: /c  
class C {  
public:  
    virtual void f1(void);  
    virtual void f2(void);  
    virtual void f3(void);  
};  
  
void C::f1(void) {}  
void C::f2(void) {}  
void C::f3(void) {}  
C q;  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4743.  
  
```  
// C4743b.cpp  
// compile with: C4743a.cpp /W1 /GL /O2  
// C4743 expected  
class C {  
public:  
    virtual void f1(void);  
    virtual void f2(void);  
    virtual void f3(void);  
    virtual void f4(void);  
    virtual void f5(void);  
};  
  
void C::f4(void) {}  
void C::f5(void) {}  
C x;  
  
int main() {}   
```