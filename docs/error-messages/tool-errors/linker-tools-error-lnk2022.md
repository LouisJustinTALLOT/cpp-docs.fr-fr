---
title: Erreur des outils Éditeur de liens LNK2022
ms.date: 11/04/2016
f1_keywords:
- LNK2022
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
ms.openlocfilehash: 187a63cb4bd22fc5e0d35523d97f438ba56b8576
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686356"
---
# <a name="linker-tools-error-lnk2022"></a>Erreur des outils Éditeur de liens LNK2022

> échec de l’opération sur les métadonnées (*HRESULT*) : *ERROR_MESSAGE*

L’éditeur de liens a détecté une erreur lors de la fusion des métadonnées. Les erreurs de métadonnées doivent être résolues pour qu’elles soient correctement liées.

Pour diagnostiquer ce problème, vous pouvez exécuter **Ildasm-Tokens** sur les fichiers objets afin de rechercher les types dont les jetons sont listés `error_message` et rechercher les différences.  Dans les métadonnées, deux types différents portant le même nom ne sont pas valides, même si l’attribut LayoutType juste est différent.

L’une des raisons de LNK2022 est lorsqu’un type (tel qu’un struct) existe dans plusieurs compilands avec le même nom, mais avec des définitions en conflit, et quand vous compilez avec [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  Dans ce cas, assurez-vous que le type a une définition identique dans toutes les compilands.  Le nom du type est indiqué dans `error_message` .

Une autre cause possible de LNK2022 est lorsque l’éditeur de liens trouve un fichier de métadonnées dans un emplacement différent de celui spécifié pour le compilateur (avec [#using](../../preprocessor/hash-using-directive-cpp.md) ). Assurez-vous que le fichier de métadonnées (. dll ou. netmodule) se trouve dans le même emplacement lorsqu’il est passé à l’éditeur de liens, comme c’était le cas lorsqu’il a été passé au compilateur.

Lors de la génération d’une application ATL, l’utilisation de la macro `_ATL_MIXED` est obligatoire dans tous les compilands, si elle est utilisée dans au moins un.

## <a name="examples"></a>Exemples

L’exemple suivant définit un type vide.

```cpp
// LNK2022_a.cpp
// compile with: /clr /c
public ref class Test {};
```

Cet exemple montre que vous ne pouvez pas lier deux fichiers de code source qui contiennent des types portant le même nom mais des définitions différentes.

L’exemple suivant génère l’LNK2022.

```cpp
// LNK2022_b.cpp
// compile with: LNK2022_a.cpp /clr /LD
// LNK2022 expected
public ref class Test {
   void func() {}
   int var;
};
```
