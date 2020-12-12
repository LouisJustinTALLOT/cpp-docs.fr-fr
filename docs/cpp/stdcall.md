---
description: 'En savoir plus sur : __stdcall'
title: __stdcall
ms.date: 10/10/2018
f1_keywords:
- __stdcall_cpp
- __stdcall
- _stdcall
helpviewer_keywords:
- __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
ms.openlocfilehash: 86ed4604eeb33c31f79ceac57b28f7f4655e78f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317933"
---
# <a name="__stdcall"></a>__stdcall

La **`__stdcall`** Convention d’appel est utilisée pour appeler les fonctions de l’API Win32. L’appelé nettoie la pile, de sorte que le compilateur effectue des `vararg` fonctions **`__cdecl`** . Les fonctions qui utilisent cette convention d’appel requièrent un prototype de fonction. Le **`__stdcall`** modificateur est spécifique à Microsoft.

## <a name="syntax"></a>Syntaxe

> *type* **`__stdcall`** de retour *Function-name*[ **`(`** *argument-List* **`)`** ]

## <a name="remarks"></a>Notes

La liste suivante illustre l'implémentation de cette convention d'appel.

|Élément|Implémentation|
|-------------|--------------------|
|Ordre de transmission des arguments|De droite à gauche|
|Convention de passage d'argument|Par valeur, à moins qu'un type pointeur ou référence soit passé.|
|Responsabilité de la maintenance de la pile|La fonction appelée enlève ses propres arguments de la pile.|
|Convention de décoration de nom|Un trait de soulignement ( `_` ) a pour préfixe le nom. Le nom est suivi du signe arobase ( `@` ) suivi du nombre d’octets (au format décimal) dans la liste d’arguments. Par conséquent, la fonction déclarée comme `int func( int a, double b )` est décorée comme suit : `_func@12`|
|Convention de conversion de casse|None|

L’option du compilateur [/gz](../build/reference/gd-gr-gv-gz-calling-convention.md) spécifie **`__stdcall`** pour toutes les fonctions qui ne sont pas déclarées explicitement avec une convention d’appel différente.

Pour la compatibilité avec les versions précédentes, **`_stdcall`** est un synonyme de, **`__stdcall`** sauf si l’option de compilateur [ `/Za` \( désactive les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

Les fonctions déclarées à l’aide du **`__stdcall`** modificateur retournent des valeurs de la même façon que les fonctions déclarées à l’aide de [`__cdecl`](../cpp/cdecl.md) .

Sur les processeurs ARM et x64, **`__stdcall`** est accepté et ignoré par le compilateur ; sur les architectures ARM et x64, par Convention, les arguments sont passés dans les registres si possible, et les arguments suivants sont passés sur la pile.

Pour les fonctions de classe non statiques, si la fonction est définie hors ligne, il n’est pas nécessaire de spécifier le modificateur de convention d’appel dans la définition hors ligne. En d’autres termes, pour les méthodes membres non statiques de classe, la convention d’appel spécifiée dans le cadre de la déclaration est utilisée par défaut au stade de la définition. Étant donné cette définition de classe,

```cpp
struct CMyClass {
   void __stdcall mymethod();
};
```

this

```cpp
void CMyClass::mymethod() { return; }
```

équivaut à ceci

```cpp
void __stdcall CMyClass::mymethod() { return; }
```

## <a name="example"></a>Exemple

Dans l’exemple suivant, l’utilisation de **`__stdcall`** entraîne la gestion de tous les `WINAPI` types de fonction comme un appel standard :

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Voir aussi

[Passage des arguments et conventions de dénomination](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
