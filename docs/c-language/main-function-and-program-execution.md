---
description: 'En savoir plus sur : fonction principale et exécution du programme'
title: Fonction main et exécution du programme
ms.date: 11/04/2016
helpviewer_keywords:
- program startup [C++]
- entry points, program
- main function, program execution
- startup code, main function
- main function
- programs [C++], terminating
ms.assetid: 5984f1bd-072d-4e06-8640-122fb1454401
ms.openlocfilehash: 00fb10526b558631c024366c09a773363bd81683
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257080"
---
# <a name="main-function-and-program-execution"></a>Fonction main et exécution du programme

Chaque programme C possède une fonction principale (main) qui doit être nommée **main**. Si votre code suit le modèle de programmation Unicode, vous pouvez utiliser la version de **main** avec les caractères larges, soit **wmain**. La fonction **main** sert de point de départ à l'exécution du programme. Elle contrôle généralement l'exécution du programme en dirigeant les appels à d'autres fonctions du programme. L'exécution d'un programme s'arrête habituellement à la fin de **main** bien qu'elle puisse se terminer à d'autres points du programme pour diverses raisons. Parfois, par exemple lorsqu'une erreur d'un certain type est détectée, vous pouvez forcer l'arrêt d'un programme. Pour cela, utilisez la fonction **exit**. Consultez *Références sur les bibliothèques Runtime C* pour plus d'informations sur l'utilisation de la fonction [exit](../c-runtime-library/reference/exit-exit-exit.md) et pour obtenir un exemple d'utilisation.

## <a name="syntax"></a>Syntaxe

```
main( int argc, char *argv[ ], char *envp[ ] )
```

## <a name="remarks"></a>Notes

Les fonctions du programme source effectuent une ou plusieurs tâches spécifiques. La fonction **main** peut appeler ces fonctions afin qu’elles effectuent leurs tâches respectives. Lorsque **main** appelle une autre fonction, elle passe le contrôle d'exécution à cette fonction afin que l'exécution commence à la première instruction de cette fonction. Une fonction retourne le contrôle à **main** lorsqu’une **`return`** instruction est exécutée ou lorsque la fin de la fonction est atteinte.

Vous pouvez déclarer toute fonction, notamment **main**, pour avoir des paramètres. Le terme « paramètre » ou « paramètre formel » désigne l'identificateur qui reçoit une valeur passée à une fonction. Pour plus d’informations sur la transmission d’arguments aux paramètres, consultez [Paramètres](../c-language/parameters.md). Lorsqu'une fonction en appelle une autre, la fonction appelée reçoit de la fonction appelante des valeurs pour ses paramètres. Ces valeurs sont appelées des arguments. Vous pouvez déclarer des paramètres formels à la fonction **main** pour lui permettre de recevoir des arguments de la ligne de commande. Pour cela, utilisez le format suivant :

Pour passer des informations à la fonction **main**, les paramètres sont traditionnellement nommés `argc` et `argv` bien que le compilateur C n'ait pas besoin de ces noms. Les types de `argc` et `argv` sont définis par le langage C. Traditionnellement, si un troisième paramètre est passé à **main**, ce paramètre est nommé `envp`. Les exemples figurant dans la suite de cette section expliquent comment utiliser ces trois paramètres pour accéder aux arguments de la ligne de commande. Les sections ci-dessous expliquent ces paramètres.

Consultez [Utilisation de wmain](../c-language/using-wmain.md) pour obtenir une description de la version de **main** avec les caractères larges.

## <a name="see-also"></a>Voir aussi

[fonction main et arguments de ligne de commande (C++)](../cpp/main-function-command-line-args.md)\
[Analyse des arguments du Command-Line C](../c-language/parsing-c-command-line-arguments.md)
