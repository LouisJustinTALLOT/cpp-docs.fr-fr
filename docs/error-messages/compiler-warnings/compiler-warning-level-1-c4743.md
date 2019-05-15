---
title: Avertissement du compilateur (niveau 1) C4743
ms.date: 05/13/2019
f1_keywords:
- C4743
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
ms.openlocfilehash: 53ead0e34b55eca44399cee09f1947a12e1eadd3
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611832"
---
# <a name="compiler-warning-level-1-c4743"></a>Avertissement du compilateur (niveau 1) C4743

«*type*'a une taille différente '*file1*'et'*fichier2*' : *nombre* et *nombre* octets

Une variable externe référencée ou définie dans deux fichiers possède des types différents dans ces fichiers, et le compilateur a déterminé que la taille de la variable dans *file1* diffère de la taille de la variable dans *fichier2*.

## <a name="remarks"></a>Notes

Il existe un cas important lorsque cet avertissement peut être émis pour C++. Si vous déclarez les mêmes types portant le même nom dans deux fichiers différents, si ces déclarations contiennent des fonctions virtuelles, et si les déclarations ne sont pas identiques, le compilateur peut émettre l’avertissement C4744 pour les tables de la fonction virtuelle. L’avertissement se produit, car il existe deux tables de tailles différentes de fonction virtuelle pour le même type, et l’éditeur de liens doit choisir un d’eux à incorporer dans le fichier exécutable.  Il est possible que cela peut entraîner de votre programme appelle la fonction virtuelle incorrecte.

Pour résoudre cet avertissement, utilisez la même définition de type ou utiliser des noms différents pour les types ou les variables.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4743. Pour le compiler, placez les deux fichiers dans le même dossier, puis exécutez  

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
