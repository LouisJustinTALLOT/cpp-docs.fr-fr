---
description: 'En savoir plus sur : erreur du compilateur C3859'
title: Erreur du compilateur C3859
ms.date: 03/08/2019
f1_keywords:
- C3859
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
ms.openlocfilehash: 25c05425072cda6924d90f08c9aeff7446a4e85b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336110"
---
# <a name="compiler-error-c3859"></a>Erreur du compilateur C3859

> plage de mémoire virtuelle dépassée pour PCH ; Recompilez avec l’option de ligne de commande'-ZM value’ou une *valeur* supérieure

La mémoire virtuelle allouée à votre en-tête précompilé est trop petite pour la quantité de données que le compilateur tente d’y placer. À compter de Visual Studio 2015, la recommandation **/ZM** n’est significative que lors de l’utilisation de la `#pragma hdrstop` directive. Dans d’autres cas, il s’agit d’une erreur parasite qui indique des problèmes de sollicitation de la mémoire virtuelle Windows.

Si votre en-tête précompilé utilise une `#pragma hdrstop` directive, utilisez l’indicateur de compilateur **/ZM** pour spécifier une valeur supérieure pour le fichier d’en-tête précompilé. Sinon, envisagez de réduire le nombre de processus de compilation parallèles dans votre Build. Pour plus d’informations, consultez [/ZM (spécifier la limite d’allocation de mémoire d’en-tête précompilé)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).
