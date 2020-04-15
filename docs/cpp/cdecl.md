---
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
ms.openlocfilehash: b4a86c49880b0c40d402c7cec863f79e24bc4dc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371565"
---
# <a name="__cdecl"></a>__cdecl

**__cdecl** est la convention d’appel par défaut pour les programmes C et CMD. Parce que la pile est nettoyée par `vararg` l’appelant, elle peut fonctionner. La **convention d’appel __cdecl** crée des exécutions plus grandes que [__stdcall,](../cpp/stdcall.md)car elle exige que chaque appel de fonction inclue le code de nettoyage des piles. La liste suivante illustre l'implémentation de cette convention d'appel. Le modificateur **__cdecl** est spécifique à Microsoft.

|Élément|Implémentation|
|-------------|--------------------|
|Ordre de transmission des arguments|De droite à gauche|
|Responsabilité de la maintenance de la pile|La fonction appelante enlève les arguments de la pile.|
|Convention de décoration de nom|Le caractère De underscore est préfixé \_aux noms, sauf lorsque _cdecl fonctions qui utilisent le lien C sont exportées.|
|Convention de conversion de casse|Aucune conversion de casse n'est effectuée.|

> [!NOTE]
> Pour plus d’informations connexes, voir [Noms décorés](../build/reference/decorated-names.md).

Placez le modificateur **__cdecl** avant une variable ou un nom de fonction. Étant donné que les conventions de nommage et d’appel C sont par défaut, la seule fois `/Gz` où vous `/Gr` devez utiliser **__cdecl** dans le code x86, c’est lorsque vous avez spécifié l’option `/Gv` (vectorcall), (stdcall) ou (fastcall). [L’option compilateur /Gd](../build/reference/gd-gr-gv-gz-calling-convention.md) force la **convention d’appel __cdecl.**

Sur les processeurs ARM et x64, **__cdecl** est acceptée mais généralement ignorée par le compilateur. Par convention sur ARM et x64, les arguments sont passés dans les registres le cas échéant, et les arguments suivants sont passés sur la pile. Dans le code x64, utilisez **__cdecl** pour remplacer l’option **compilateur /Gv** et utilisez la convention d’appel x64 par défaut.

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

Pour la compatibilité avec les versions précédentes, **le cdecl** et **le _cdecl** sont synonymes de **__cdecl** à moins que l’option compilateur [/Za \(Disable extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) ne soit spécifiée.

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
