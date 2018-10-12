---
title: __cdecl | Microsoft Docs
ms.custom: ''
ms.date: 10/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __cdecl_cpp
- __cdecl
- _cdecl
- cdecl
dev_langs:
- C++
helpviewer_keywords:
- __cdecl keyword [C++]
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 085d8a49ed3c66f96bf8c2b8bdae7ca54cf3bef6
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163775"
---
# <a name="cdecl"></a>__cdecl

**Section spécifique à Microsoft**

**__cdecl** est la valeur par défaut de convention d’appel pour les programmes C et C++. Étant donné que la pile est nettoyée par l’appelant, il peut faire `vararg` fonctions. Le **__cdecl** convention d’appel crée des exécutables plus grands que [__stdcall](../cpp/stdcall.md), car elle exige de chaque appel de fonction pour inclure du code de nettoyage de pile. La liste suivante illustre l’implémentation de cette convention d’appel.

|Élément|Implémentation|
|-------------|--------------------|
|Ordre de transmission des arguments|De droite à gauche|
|Responsabilité de la maintenance de la pile|La fonction appelante enlève les arguments de la pile.|
|Convention de décoration de nom|Caractère de soulignement (_) est préfixé aux noms, sauf quand \__cdecl les fonctions qui utilisent une liaison C sont exportées.|
|Convention de conversion de casse|Aucune conversion de casse n'est effectuée.|

> [!NOTE]
>  Pour plus d’informations, consultez [noms décorés](../build/reference/decorated-names.md).

Place le **__cdecl** modificateur avant une variable ou un nom de fonction. Étant donné que les noms et conventions d’appel C sont la valeur par défaut, le seul moment où vous devez utiliser **__cdecl** dans x86 code est lorsque vous avez spécifié le `/Gv` (vectorcall), `/Gz` (stdcall) ou `/Gr` (fastcall) option du compilateur. Le [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md) du compilateur option force le **__cdecl** convention d’appel.

Sur ARM et x64 processeurs, **__cdecl** est accepté mais en général ignoré par le compilateur. Par convention sur ARM et x64, les arguments sont passés dans les registres le cas échéant, et les arguments suivants sont passés sur la pile. Dans x64 de code, utilisez **__cdecl** pour remplacer le **GV** option du compilateur et l’utilisation de la convention d’appel par défaut x64.

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

Pour assurer la compatibilité avec les versions précédentes, **cdecl** et **_cdecl** sont un synonyme de **__cdecl** , sauf si option du compilateur [/Za \(désactiver extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifié.

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