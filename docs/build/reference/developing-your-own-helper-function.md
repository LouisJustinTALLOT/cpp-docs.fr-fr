---
title: Développement de votre propre fonction d'assistance
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
ms.openlocfilehash: 2601aff6b53e9ad3a970dbe1be008efdd7008ef8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424429"
---
# <a name="developing-your-own-helper-function"></a>Développement de votre propre fonction d'assistance

Voulez-vous fournir votre propre version de la routine pour effectuer un traitement particulier selon les noms des DLL ou des importations. Il existe deux méthodes d’effectuer cette opération : codage vous-même, éventuellement en fonction le code fourni, ou une connexion simplement la version fournie à l’aide des raccordements de notification précédemment.

## <a name="code-your-own"></a>Code de votre propre

Cela est assez simple, car vous pouvez utiliser essentiellement le code fourni à titre indicatif pour une nouvelle. Bien entendu, doit respecter les conventions d’appel et retour vers les thunks générés par l’éditeur de liens, elle doit retourner un pointeur de fonction approprié. Une fois dans votre code, vous pouvez faire pratiquement tout ce que vous voulez afin de satisfaire l’appel ou de tirer parti de l’appel.

## <a name="use-the-start-processing-notification-hook"></a>Utilisez le traitement de raccordement de Notification de démarrage

Il sera probablement plus facile de simplement fournir un nouveau pointeur à une fonction de raccordement fournie par l’utilisateur de notification qui reçoit les mêmes valeurs que l’assistance par défaut lors de la notification dliStartProcessing. À ce stade, la fonction de raccordement peut devenir la nouvelle fonction d’assistance, comme un retour réussi à l’assistance par défaut sera ignorer tout traitement supplémentaire dans l’assistance par défaut.

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les DLL à chargement différé](../../build/reference/linker-support-for-delay-loaded-dlls.md)
