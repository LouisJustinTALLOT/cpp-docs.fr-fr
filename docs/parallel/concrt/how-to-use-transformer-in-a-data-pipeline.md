---
title: 'Comment : utiliser la classe transformer dans un pipeline de données'
ms.date: 11/04/2016
helpviewer_keywords:
- transformer class, example
- data pipelines, using transformer [Concurrency Runtime]
- using transformer in data pipelines [Concurrency Runtime]
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
ms.openlocfilehash: 4eb490ecf51abea324f20395279bff2d74b7af77
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215853"
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>Comment : utiliser la classe transformer dans un pipeline de données

Cette rubrique contient un exemple de base qui montre comment utiliser la classe [Concurrency :: transformer](../../parallel/concrt/reference/transformer-class.md) dans un pipeline de données. Pour obtenir un exemple plus complet qui utilise un pipeline de données pour le traitement de l’image, consultez [procédure pas à pas : création d’un réseau de traitement d’image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

Le *traitement en pipeline des données* est un modèle courant dans la programmation simultanée. Un pipeline de données se compose d’une série d’étapes, où chaque étape exécute du travail, puis passe le résultat de ce travail à l’étape suivante. La `transformer` classe est un composant clé dans les pipelines de données, car elle reçoit une valeur d’entrée, effectue un travail sur cette valeur, puis produit un résultat pour un autre composant à utiliser.

## <a name="example"></a>Exemple

Cet exemple utilise le pipeline de données suivant pour effectuer une série de transformations en fonction d’une valeur d’entrée initiale :

1. La première étape calcule la valeur absolue de son entrée.

1. La deuxième étape calcule la racine carrée de son entrée.

1. La troisième étape calcule le carré de son entrée.

1. L’étape intermédiaire nie son entrée.

1. La cinquième étape écrit le résultat final dans une mémoire tampon de message.

Enfin, l’exemple imprime le résultat du pipeline sur la console.

[!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]

Cet exemple produit la sortie suivante :

```Output
The result is -42.
```

Il est courant qu’une étape d’un pipeline de données génère une valeur dont le type diffère de sa valeur d’entrée. Dans cet exemple, la deuxième étape prend une valeur de type **`int`** comme entrée et génère la racine carrée de cette valeur (a **`double`** ) comme sortie.

> [!NOTE]
> Dans cet exemple, le pipeline de données est à titre d’illustration. Étant donné que chaque opération de transformation effectue peu de travail, la surcharge requise pour effectuer le passage de messages peut contrebalancer les avantages de l’utilisation d’un pipeline de données.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `data-pipeline.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc data-pipeline. cpp**

## <a name="see-also"></a>Voir aussi

[bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Procédure pas à pas : création d’un réseau de traitement d’image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)
