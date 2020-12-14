---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4743'
title: Avertissement du compilateur (niveau 1) C4743
ms.date: 05/13/2019
f1_keywords:
- C4743
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
ms.openlocfilehash: a8c8bcd4ef0e4d7084da34e033be4194da11727f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228480"
---
# <a name="compiler-warning-level-1-c4743"></a>Avertissement du compilateur (niveau 1) C4743

'*type*'a une taille différente dans'*fichier1*'et'*fichier2*' : *nombre* et octets 

Une variable externe référencée ou définie dans deux fichiers a des types différents dans ces fichiers, et le compilateur a déterminé que la taille de la variable dans *fichier1* est différente de la taille de la variable dans *fichier2*.

## <a name="remarks"></a>Notes

Il existe un cas important lorsque cet avertissement peut être émis pour C++. Si vous déclarez les mêmes types avec le même nom dans deux fichiers différents, si ces déclarations contiennent des fonctions virtuelles et si les déclarations ne sont pas les mêmes, le compilateur peut émettre des C4744 d’avertissement pour les tables de fonctions virtuelles. L’avertissement se produit, car il existe deux tables de fonctions virtuelles de taille différente pour le même type, et l’éditeur de liens doit choisir l’un d’entre eux pour incorporer dans l’exécutable.  Il est possible que votre programme appelle la fonction virtuelle incorrecte.

Pour résoudre cet avertissement, utilisez la même définition de type ou utilisez des noms différents pour les types ou les variables.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4743. Pour le compiler, placez les deux fichiers dans le même dossier, puis exécutez  

```cmd
cl /EHsc /W1 /GL /O2 C4743a.cpp C4743b.cpp
```

```cpp
// C4743a.cpp
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

```cpp
// C4743b.cpp
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
