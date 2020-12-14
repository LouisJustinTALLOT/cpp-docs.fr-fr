---
description: 'En savoir plus sur : __fastcall'
title: __fastcall
ms.date: 12/17/2018
f1_keywords:
- __fastcall_cpp
- __fastcall
- _fastcall
helpviewer_keywords:
- __fastcall keyword [C++]
ms.assetid: bb5b9c8a-dfad-450c-9119-0ac2bc59544f
ms.openlocfilehash: 6f4c4f533f0d2337323d486cc9c433898a19e6a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242598"
---
# <a name="__fastcall"></a>__fastcall

**Spécifique à Microsoft**

La **`__fastcall`** Convention d’appel spécifie que les arguments des fonctions doivent être passés dans les registres, lorsque cela est possible. Cette convention d’appel s’applique uniquement à l’architecture x86. La liste suivante illustre l'implémentation de cette convention d'appel.

|Élément|Implémentation|
|-------------|--------------------|
|Ordre de transmission des arguments|Les deux premiers DWORD ou arguments plus petits qui figurent dans la liste d’arguments de gauche à droite sont transmis dans les registres ECX et EDX ; tous les autres arguments sont transmis sur la pile de droite à gauche.|
|Responsabilité de la maintenance de la pile|La fonction appelée enlève les arguments de la pile.|
|Convention de décoration de nom|Arobase ( \@ ) a pour préfixe les noms ; un arobase suivi du nombre d’octets (au format décimal) dans la liste de paramètres est précédé d’un suffixe Name.|
|Convention de conversion de casse|Aucune conversion de casse n'est effectuée.|

> [!NOTE]
> Les futures versions du compilateur peuvent utiliser des registres pour stocker les paramètres.

L’utilisation de l’option du compilateur [/GR](../build/reference/gd-gr-gv-gz-calling-convention.md) provoque la compilation de chaque fonction du module en tant que, **`__fastcall`** sauf si la fonction est déclarée à l’aide d’un attribut en conflit ou si le nom de la fonction est `main` .

Le **`__fastcall`** mot clé est accepté et ignoré par les compilateurs qui ciblent les architectures ARM et x64 ; sur un processeur x64, par Convention, les quatre premiers arguments sont passés dans les registres si possible, et des arguments supplémentaires sont passés sur la pile. Pour plus d’informations, consultez [Convention d’appel x64](../build/x64-calling-convention.md). Sur un processeur ARM, jusqu'à quatre arguments entiers et huit arguments à virgule flottante peuvent être transmis dans les registres, et des arguments supplémentaires sont transmis sur la pile.

Pour les fonctions de classe non statiques, si la fonction est définie hors ligne, il n’est pas nécessaire de spécifier le modificateur de convention d’appel dans la définition hors ligne. En d’autres termes, pour les méthodes membres non statiques de classe, la convention d’appel spécifiée dans le cadre de la déclaration est utilisée par défaut au stade de la définition. Compte tenu de la définition de classe suivante :

```cpp
struct CMyClass {
   void __fastcall mymethod();
};
```

le code suivant :

```cpp
void CMyClass::mymethod() { return; }
```

équivaut au code :

```cpp
void __fastcall CMyClass::mymethod() { return; }
```

Pour la compatibilité avec les versions précédentes, **_fastcall** est un synonyme de, **`__fastcall`** sauf si l’option de compilateur [/za \( Désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

## <a name="example"></a>Exemple

Dans l'exemple suivant, la fonction `DeleteAggrWrapper` correspond aux arguments transmis dans les registres :

```cpp
// Example of the __fastcall keyword
#define FASTCALL    __fastcall

void FASTCALL DeleteAggrWrapper(void* pWrapper);
// Example of the __ fastcall keyword on function pointer
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Passage des arguments et conventions de dénomination](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
