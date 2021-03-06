---
description: 'En savoir plus sur : `selectany`'
title: selectany
ms.date: 11/04/2016
f1_keywords:
- selectany_cpp
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
ms.openlocfilehash: e17ad5787211aacbb206d5e68ba355047711b96a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319337"
---
# `selectany`

**Spécifique à Microsoft**

Indique au compilateur que l'élément de données global déclaré (variable ou objet) est un COMDAT pick-any (une fonction packagée).

## <a name="syntax"></a>Syntaxe

> **`__declspec( selectany )`***déclarateur*

## <a name="remarks"></a>Notes

Au moment d'effectuer le lien, si plusieurs définitions d'un COMDAT s'affichent, l'éditeur de liens en choisit un et ignore le reste. Si l’option de l’éditeur [`/OPT:REF`](../build/reference/opt-optimizations.md) de liens (optimisations) est sélectionnée, l’élimination COMDAT aura lieu pour supprimer tous les éléments de données non référencés dans la sortie de l’éditeur de liens.

Les constructeurs et l'assignation par fonction globale ou méthodes statiques dans la déclaration ne créent pas de référence et n'empêchent pas la suppression /OPT:REF. Les effets secondaires d'un tel code ne doivent pas créer de dépendances quand il n'existe aucune autre référence à des données.

Pour les objets globaux initialisés dynamiquement, **`selectany`** ignore également le code d’initialisation d’un objet non référencé.

Un élément de données global ne peut généralement être initialisé qu'une seule fois dans un projet EXE ou DLL. **`selectany`** peut être utilisé pour initialiser des données globales définies par des en-têtes, lorsque le même en-tête apparaît dans plusieurs fichiers sources. **`selectany`** est disponible dans les compilateurs C et C++.

> [!NOTE]
> **`selectany`** ne peut être appliqué qu’à l’initialisation réelle des éléments de données globaux qui sont visibles de l’extérieur.

## <a name="example-selectany-attribute"></a>Exemple : `selectany` attribut

Ce code montre comment utiliser l' **`selectany`** attribut :

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

## <a name="example-use-selectany-attribute-to-ensure-data-comdat-folding"></a>Exemple : utiliser l' `selectany` attribut pour garantir le repli des données COMDAT

Ce code montre comment utiliser l' **`selectany`** attribut pour garantir le repli des données COMDAT lorsque vous utilisez également l’option de l' [`/OPT:ICF`](../build/reference/opt-optimizations.md) éditeur de liens. Notez que les données doivent être marquées avec **`selectany`** et placées dans une **`const`** section (ReadOnly). Vous devez spécifier explicitement la section en lecture seule.

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

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[`__declspec`](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
