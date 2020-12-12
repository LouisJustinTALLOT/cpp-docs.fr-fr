---
description: 'En savoir plus sur : développement de votre propre fonction d’assistance'
title: Développement de votre propre fonction d'assistance
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
ms.openlocfilehash: da536d13da9a596c5667c3fa84311b73e66d71ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201454"
---
# <a name="developing-your-own-helper-function"></a>Développement de votre propre fonction d'assistance

Vous pouvez fournir votre propre version de la routine pour effectuer un traitement spécifique en fonction des noms de la DLL ou des importations. Il existe deux méthodes pour cela : coder votre propre, éventuellement en fonction du code fourni, ou simplement raccorder la version fournie à l’aide des hooks de notification détaillés précédemment.

## <a name="code-your-own"></a>Coder votre propre code

C’est assez simple, car vous pouvez essentiellement utiliser le code fourni comme indication pour le nouveau. Bien sûr, il doit adhérer aux conventions d’appel et, s’il retourne aux thunks générés par l’éditeur de liens, il doit retourner un pointeur de fonction approprié. Une fois dans votre code, vous pouvez faire à peu près tout ce que vous souhaitez pour satisfaire l’appel ou sortir de l’appel.

## <a name="use-the-start-processing-notification-hook"></a>Utiliser le hook de notification de démarrage du traitement

Il sera probablement plus facile de fournir simplement un nouveau pointeur vers une fonction de raccordement de notification fournie par l’utilisateur qui reçoit les mêmes valeurs que le programme d’assistance par défaut sur le dliStartProcessing de notification. À ce stade, la fonction de raccordement peut devenir essentiellement la nouvelle fonction d’assistance, car un retour correct à l’assistance par défaut contourne tout traitement supplémentaire dans le programme d’assistance par défaut.

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les dll Delay-Loaded](linker-support-for-delay-loaded-dlls.md)
