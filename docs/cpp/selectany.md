---
title: selectany
ms.date: 11/04/2016
f1_keywords:
- selectany_cpp
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
ms.openlocfilehash: e8ca82900ffd16264aca494950d4793029e55d9c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365597"
---
# <a name="selectany"></a>selectany

**Microsoft Spécifique**

Indique au compilateur que l'élément de données global déclaré (variable ou objet) est un COMDAT pick-any (une fonction packagée).

## <a name="syntax"></a>Syntaxe

```
__declspec( selectany ) declarator
```

## <a name="remarks"></a>Notes

Au moment d'effectuer le lien, si plusieurs définitions d'un COMDAT s'affichent, l'éditeur de liens en choisit un et ignore le reste. Si l’option de liaison [/OPT:REF](../build/reference/opt-optimizations.md) (Optimizations) est sélectionnée, l’élimination COMDAT se produira pour supprimer tous les éléments de données non réfrés dans la sortie du linker.

Les constructeurs et l'assignation par fonction globale ou méthodes statiques dans la déclaration ne créent pas de référence et n'empêchent pas la suppression /OPT:REF. Les effets secondaires d'un tel code ne doivent pas créer de dépendances quand il n'existe aucune autre référence à des données.

Pour les objets globals dynamiquement parasés, **selectany** jettera également le code d’initialisation d’un objet non référé.

Un élément de données global ne peut généralement être initialisé qu'une seule fois dans un projet EXE ou DLL. **selectany** peut être utilisé pour initialiser les données globales définies par des en-têtes, lorsque le même en-tête apparaît dans plus d’un fichier source. **selectany** est disponible dans les compilateurs C et CMD.

> [!NOTE]
> **selectany** ne peut être appliqué qu’à la initialisation réelle des éléments de données globaux qui sont visibles à l’extérieur.

## <a name="example"></a>Exemple

Ce code montre comment utiliser l’attribut **selectany** :

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

Ce code montre comment utiliser **l’attribut selectany** pour assurer le pliage des données COMDAT lorsque vous utilisez également l’option de liaison [/OPT:ICF.](../build/reference/opt-optimizations.md) Notez que les données doivent être marquées avec **selectany** et placées dans une section **const** (lire). Vous devez spécifier explicitement la section en lecture seule.

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

**END Microsoft Spécifique**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
