---
title: instanciation explicite
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: 0b1290bc23c56c0f35ddd3bb93e37ce4f5f0d2ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361961"
---
# <a name="explicit-instantiation"></a>instanciation explicite

Vous pouvez utiliser l’instantanéisation explicite pour créer une instantanéisation d’une classe ou d’une fonction modélisée sans l’utiliser réellement dans votre code. Parce que cela est utile lorsque vous créez des fichiers de bibliothèque (.lib) qui utilisent des modèles pour la distribution, définitions de modèles non corroborées ne sont pas mis dans les fichiers objet (.obj).

Ce code instantané `MyStack` explicitement pour les variables **int** et six éléments:

```cpp
template class MyStack<int, 6>;
```

Cette déclaration crée une `MyStack` instantanéisation de sans réserver de stockage pour un objet. Le code est généré pour tous les membres.

La ligne suivante n’instantanéise explicitement que la fonction de membre constructeur :

```cpp
template MyStack<int, 6>::MyStack( void );
```

Vous pouvez explicitement instantané les modèles de fonction en utilisant un argument de type spécifique pour les re-déclarer, comme le montre l’exemple dans [l’instantiation de modèle de fonction](../cpp/function-template-instantiation.md).

Vous pouvez utiliser le mot clé **extern pour** empêcher l’instantanéisation automatique des membres. Par exemple :

```cpp
extern template class MyStack<int, 6>;
```

De même, vous pouvez marquer les membres spécifiques comme étant externes et non instantanés :

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

Vous pouvez utiliser le mot clé **extern pour** empêcher le compilateur de générer le même code d’instantanéisation dans plus d’un module d’objet. Vous devez instantané la fonction de modèle en utilisant les paramètres explicites spécifiés de modèle dans au moins un module lié si la fonction est appelée, ou vous obtiendrez une erreur de liaison lorsque le programme est construit.

> [!NOTE]
> Le mot clé **extern** dans la spécialisation ne s’applique qu’aux fonctions des membres définies en dehors du corps de la classe. Les fonctions définies à l’intérieur de la déclaration de classe sont considérées comme des fonctions inlines et sont toujours instantanées.

## <a name="see-also"></a>Voir aussi

[Modèles de fonction](../cpp/function-templates.md)
