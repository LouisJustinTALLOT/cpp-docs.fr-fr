---
description: 'En savoir plus sur : __cdecl'
title: __cdecl
ms.date: 10/09/2018
f1_keywords:
- __cdecl_cpp
- __cdecl
- _cdecl
- cdecl
helpviewer_keywords:
- __cdecl keyword [C++]
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
ms.openlocfilehash: de6d34aa70353f65191c0c36c790d517a1fbbf0e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308573"
---
# <a name="__cdecl"></a>__cdecl

**`__cdecl`** est la Convention d’appel par défaut pour les programmes C et C++. Étant donné que la pile est nettoyée par l’appelant, elle peut faire des `vararg` fonctions. La **`__cdecl`** Convention d’appel crée des exécutables plus grands que [__stdcall](../cpp/stdcall.md), car elle requiert que chaque appel de fonction inclue le code de nettoyage de la pile. La liste suivante illustre l'implémentation de cette convention d'appel. Le **`__cdecl`** modificateur est spécifique à Microsoft.

|Élément|Implémentation|
|-------------|--------------------|
|Ordre de transmission des arguments|De droite à gauche|
|Responsabilité de la maintenance de la pile|La fonction appelante enlève les arguments de la pile.|
|Convention de décoration de nom|Le trait de soulignement (_) est préfixé aux noms, sauf lorsque \_ _cdecl fonctions qui utilisent la liaison C sont exportées.|
|Convention de conversion de casse|Aucune conversion de casse n'est effectuée.|

> [!NOTE]
> Pour obtenir des informations connexes, consultez [noms décorés](../build/reference/decorated-names.md).

Placez le **`__cdecl`** modificateur avant une variable ou un nom de fonction. Comme les conventions d’affectation de noms et d’appel C sont définies par défaut, la seule fois où vous devez utiliser **`__cdecl`** dans le code x86 est lorsque vous avez spécifié l' `/Gv` option du compilateur (vectorcall), `/Gz` (stdcall) ou `/Gr` (fastcall). L’option du compilateur [/gd](../build/reference/gd-gr-gv-gz-calling-convention.md) force la **`__cdecl`** Convention d’appel.

Sur les processeurs ARM et x64, **`__cdecl`** est accepté, mais est généralement ignoré par le compilateur. Par convention sur ARM et x64, les arguments sont passés dans les registres le cas échéant, et les arguments suivants sont passés sur la pile. Dans le code x64, utilisez **`__cdecl`** pour remplacer l’option du compilateur **/GV** et utilisez la Convention d’appel x64 par défaut.

Pour les fonctions de classe non statiques, si la fonction est définie hors ligne, il n’est pas nécessaire de spécifier le modificateur de convention d’appel dans la définition hors ligne. En d’autres termes, pour les méthodes membres non statiques de classe, la convention d’appel spécifiée dans le cadre de la déclaration est utilisée par défaut au stade de la définition. Compte tenu de la définition de classe suivante :

```cpp
struct CMyClass {
   void __cdecl mymethod();
};
```

le code suivant :

```cpp
void CMyClass::mymethod() { return; }
```

équivaut au code :

```cpp
void __cdecl CMyClass::mymethod() { return; }
```

Pour la compatibilité avec les versions précédentes, **cdecl** et **_cdecl** sont un synonyme de, **`__cdecl`** sauf si l’option de compilateur [/za \( Désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

## <a name="example"></a>Exemple

Dans l’exemple suivant, le compilateur est chargé d’utiliser les conventions de nommage et d’appel du langage C pour la fonction `system`.

```cpp
// Example of the __cdecl keyword on function
int __cdecl system(const char *);
// Example of the __cdecl keyword on function pointer
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Voir aussi

[Passage des arguments et conventions de dénomination](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
