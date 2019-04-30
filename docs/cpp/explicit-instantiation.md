---
title: instanciation explicite
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: 45661653b4b8f1a4f94ece1c53aa86f4a431700b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392204"
---
# <a name="explicit-instantiation"></a>instanciation explicite

Vous pouvez utiliser l’instanciation explicite pour créer une instanciation d’une classe basée sur un modèle ou d’une fonction sans réellement l’utiliser dans votre code. Étant donné que cela est utile lorsque vous créez bibliothèque (.lib) les fichiers qui utilisent les modèles pour la distribution, définitions de modèle non instancié ne sont pas placées dans des fichiers objet (.obj).

Ce code instancie explicitement `MyStack` pour **int** variables et six éléments :

```cpp
template class MyStack<int, 6>;
```

Cette instruction crée une instanciation de `MyStack` sans réserver tout stockage pour un objet. Code est généré pour tous les membres.

La ligne suivante instancie explicitement que la fonction membre de constructeur :

```cpp
template MyStack<int, 6>::MyStack( void );
```

Vous pouvez instancier explicitement des modèles de fonction à l’aide d’un argument de type spécifique à nouveau les déclarer, comme indiqué dans l’exemple de [instanciation du modèle de fonction](../cpp/function-template-instantiation.md).

Vous pouvez utiliser la **extern** mot clé pour empêcher l’instanciation automatique des membres. Exemple :

```cpp
extern template class MyStack<int, 6>;
```

De même, vous pouvez marquer comme étant non instanciée et externes des membres spécifiques :

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

Vous pouvez utiliser la **extern** mot clé pour empêcher le compilateur de générer le même code d’instanciation dans plusieurs modules de l’objet. Vous devez instancier la fonction de modèle en utilisant les paramètres de modèle explicite spécifié au moins un module lié si la fonction est appelée, ou vous obtiendrez une erreur de l’éditeur de liens lorsque le programme est généré.

> [!NOTE]
>  Le **extern** mot clé dans la spécialisation s’applique uniquement aux fonctions membres définies en dehors du corps de la classe. Fonctions définies à l’intérieur de la déclaration de classe sont considérés comme des fonctions inline et sont toujours instanciées.

## <a name="see-also"></a>Voir aussi

[Modèles de fonctions](../cpp/function-templates.md)