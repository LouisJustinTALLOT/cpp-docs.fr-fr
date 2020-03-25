---
title: instanciation explicite
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: dbe8bebf91a174e07c7c5cce8e9caf1cf3432edf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180028"
---
# <a name="explicit-instantiation"></a>instanciation explicite

Vous pouvez utiliser l’instanciation explicite pour créer une instanciation d’une classe ou d’une fonction basée sur un modèle sans réellement l’utiliser dans votre code. Étant donné que cela est utile lorsque vous créez des fichiers de bibliothèque (. lib) qui utilisent des modèles pour la distribution, les définitions de modèle non instanciées ne sont pas placées dans des fichiers objets (. obj).

Ce code instancie explicitement `MyStack` pour les variables **int** et les six éléments suivants :

```cpp
template class MyStack<int, 6>;
```

Cette instruction crée une instanciation de `MyStack` sans réserver de stockage pour un objet. Du code est généré pour tous les membres.

La ligne suivante instancie explicitement uniquement la fonction membre de constructeur :

```cpp
template MyStack<int, 6>::MyStack( void );
```

Vous pouvez instancier explicitement des modèles de fonction à l’aide d’un argument de type spécifique pour les redéclarer, comme indiqué dans l’exemple de l' [instanciation du modèle de fonction](../cpp/function-template-instantiation.md).

Vous pouvez utiliser le mot clé **extern** pour empêcher l’instanciation automatique des membres. Par exemple :

```cpp
extern template class MyStack<int, 6>;
```

De même, vous pouvez marquer des membres spécifiques comme étant externes et non instanciés :

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

Vous pouvez utiliser le mot clé **extern** pour empêcher le compilateur de générer le même code d’instanciation dans plusieurs modules objet. Vous devez instancier la fonction de modèle en utilisant les paramètres de modèle explicites spécifiés dans au moins un module lié si la fonction est appelée, ou vous obtiendrez une erreur de l’éditeur de liens lors de la génération du programme.

> [!NOTE]
>  Le mot clé **extern** de la spécialisation s’applique uniquement aux fonctions membres définies en dehors du corps de la classe. Les fonctions définies à l’intérieur de la déclaration de classe sont considérées comme des fonctions inline et sont toujours instanciées.

## <a name="see-also"></a>Voir aussi

[Modèles de fonctions](../cpp/function-templates.md)
