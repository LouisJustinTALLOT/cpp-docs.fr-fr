---
title: __stdcall
ms.date: 10/10/2018
f1_keywords:
- __stdcall_cpp
- __stdcall
- _stdcall
helpviewer_keywords:
- __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
ms.openlocfilehash: b9efac6f729a78db945ff3bd9ab16ebe315b7a5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560639"
---
# <a name="stdcall"></a>__stdcall

**Section spécifique à Microsoft**

Le **__stdcall** convention d’appel est utilisée pour appeler des fonctions API Win32. L’appelé nettoie la pile, donc le compilateur est `vararg` fonctions **__cdecl**. Les fonctions qui utilisent cette convention d’appel requièrent un prototype de fonction.

## <a name="syntax"></a>Syntaxe

> *type de retour*  **\_ \_stdcall** *nom de la fonction*[**(** *liste d’arguments* **)** ]

## <a name="remarks"></a>Notes

La liste suivante illustre l’implémentation de cette convention d’appel.

|Élément|Implémentation|
|-------------|--------------------|
|Ordre de transmission des arguments|De droite à gauche|
|Convention de passage d'argument|Par valeur, à moins qu'un type pointeur ou référence soit passé.|
|Responsabilité de la maintenance de la pile|La fonction appelée enlève ses propres arguments de la pile.|
|Convention de décoration de nom|Un trait de soulignement (_) est ajouté en préfixe au nom. Le nom est suivi de l'arobase (@), suivi du nombre d'octets (au format décimal) dans la liste d'arguments. Par conséquent, la fonction déclarée comme `int func( int a, double b )` est décorée comme suit : `_func@12`|
|Convention de conversion de casse|Aucun.|

Le [/Gz](../build/reference/gd-gr-gv-gz-calling-convention.md) option du compilateur spécifie **__stdcall** pour toutes les fonctions ne sont pas explicitement déclarées avec une autre convention d’appel.

Pour assurer la compatibilité avec les versions précédentes, **_stdcall** est un synonyme de **__stdcall** , sauf si option du compilateur [/Za \(désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifié.

Les fonctions déclarées à l’aide de la **__stdcall** la même façon que les fonctions déclarées à l’aide des valeurs de retour de modificateur [__cdecl](../cpp/cdecl.md).

Sur ARM et x64 processeurs, **__stdcall** est accepté et ignoré par le compilateur ; sur ARM et x64 architectures, par convention, les arguments sont passés dans les registres quand cela est possible, et les arguments suivants sont passés sur la pile.

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

Dans l’exemple suivant, l’utilisation de **__stdcall** entraîne tous `WINAPI` types de fonction comme un appel standard :

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Voir aussi

[Passage des arguments et conventions de dénomination](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)