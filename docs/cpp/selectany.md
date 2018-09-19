---
title: selectany | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- selectany_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee48bf8a739f7fc024604ba178b56da99844861b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102337"
---
# <a name="selectany"></a>selectany

**Section spécifique à Microsoft**

Indique au compilateur que l'élément de données global déclaré (variable ou objet) est un COMDAT pick-any (une fonction packagée).

## <a name="syntax"></a>Syntaxe

```
__declspec( selectany ) declarator
```

## <a name="remarks"></a>Notes

Au moment d'effectuer le lien, si plusieurs définitions d'un COMDAT s'affichent, l'éditeur de liens en choisit un et ignore le reste. Si l’option de l’éditeur de liens [/OPT : REF](../build/reference/opt-optimizations.md) (optimisations) est sélectionnée, puis l’élimination COMDAT se produit pour supprimer tous les éléments de données non référencées dans la sortie de l’éditeur de liens.

Les constructeurs et l'assignation par fonction globale ou méthodes statiques dans la déclaration ne créent pas de référence et n'empêchent pas la suppression /OPT:REF. Les effets secondaires d'un tel code ne doivent pas créer de dépendances quand il n'existe aucune autre référence à des données.

Pour les objets dynamiquement initialisés et globaux, **selectany** supprimera le code d’initialisation d’un objet non référencé, également.

Un élément de données global ne peut généralement être initialisé qu'une seule fois dans un projet EXE ou DLL. **selectany** peuvent être utilisées pour initialiser des données globales définies par les en-têtes, lorsque le même en-tête apparaît dans plusieurs fichiers source. **selectany** est disponible dans les compilateurs C et C++.

> [!NOTE]
>  **selectany** peut uniquement être appliqué à l’initialisation réelle global des éléments de données qui sont visibles.

## <a name="example"></a>Exemple

Ce code montre comment utiliser le **selectany** attribut :

```cpp
//Correct - x1 is initialized and externally visible
__declspec(selectany) int x1=1;

//Incorrect - const is by default static in C++, so
//x2 is not visible externally (This is OK in C, since
//const is not by default static in C)
const __declspec(selectany) int x2 =2;

//Correct - x3 is extern const, so externally visible
extern const __declspec(selectany) int x3=3;

//Correct - x4 is extern const, so it is externally visible
extern const int x4;
const __declspec(selectany) int x4=4;

//Incorrect - __declspec(selectany) is applied to the uninitialized
//declaration of x5
extern __declspec(selectany) int x5;

// OK: dynamic initialization of global object
class X {
public:
X(int i){i++;};
int i;
};

__declspec(selectany) X x(1);
```

## <a name="example"></a>Exemple

Ce code montre comment utiliser le **selectany** attribut pour garantir le pliage des données COMDAT lorsque vous utilisez également le [/OPT : ICF](../build/reference/opt-optimizations.md) option de l’éditeur de liens. Notez que les données doivent être marquées avec **selectany** et placé dans un **const** section (en lecture seule). Vous devez spécifier explicitement la section en lecture seule.

```cpp
// selectany2.cpp
// in the following lines, const marks the variables as read only
__declspec(selectany) extern const int ix = 5;
__declspec(selectany) extern const int jx = 5;
int main() {
   int ij;
   ij = ix + jx;
}
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)