---
title: Développement de votre propre fonction d’assistance | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- helper functions
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d95434c51bdfca07e48714c8c1e13bcdb64dc02f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715999"
---
# <a name="developing-your-own-helper-function"></a>Développement de votre propre fonction d'assistance

Voulez-vous fournir votre propre version de la routine pour effectuer un traitement particulier selon les noms des DLL ou des importations. Il existe deux méthodes d’effectuer cette opération : codage vous-même, éventuellement en fonction le code fourni, ou une connexion simplement la version fournie à l’aide des raccordements de notification précédemment.

## <a name="code-your-own"></a>Code de votre propre

Cela est assez simple, car vous pouvez utiliser essentiellement le code fourni à titre indicatif pour une nouvelle. Bien entendu, doit respecter les conventions d’appel et retour vers les thunks générés par l’éditeur de liens, elle doit retourner un pointeur de fonction approprié. Une fois dans votre code, vous pouvez faire pratiquement tout ce que vous voulez afin de satisfaire l’appel ou de tirer parti de l’appel.

## <a name="use-the-start-processing-notification-hook"></a>Utilisez le traitement de raccordement de Notification de démarrage

Il sera probablement plus facile de simplement fournir un nouveau pointeur à une fonction de raccordement fournie par l’utilisateur de notification qui reçoit les mêmes valeurs que l’assistance par défaut lors de la notification dliStartProcessing. À ce stade, la fonction de raccordement peut devenir la nouvelle fonction d’assistance, comme un retour réussi à l’assistance par défaut sera ignorer tout traitement supplémentaire dans l’assistance par défaut.

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les DLL à chargement différé](../../build/reference/linker-support-for-delay-loaded-dlls.md)