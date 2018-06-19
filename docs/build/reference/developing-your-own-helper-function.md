---
title: Développement de votre propre fonction d’assistance | Documents Microsoft
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
ms.openlocfilehash: e6b8e397fecc8f14140cd7c86217421d5aa1a749
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371396"
---
# <a name="developing-your-own-helper-function"></a>Développement de votre propre fonction d'assistance
Voulez-vous fournir votre propre version de la routine de traitement spécifique en fonction des noms des DLL ou des importations. Il existe deux méthodes d’effectuer cette opération : codage de votre choix, éventuellement basée sur le code fourni, ou simplement placer la version fournie à l’aide des raccordements de notification précédemment.  
  
 Code de votre propre  
 Cela est assez simple, car vous pouvez essentiellement utiliser le code fourni à titre indicatif pour une nouvelle. Bien entendu, il doit respecter les conventions d’appel et s’il retourne à la conversion de code généré par l’éditeur de liens, elle doit retourner un pointeur fonction correct. Une fois dans votre code, vous pouvez effectuer pratiquement tout ce que vous voulez afin de répondre à l’appel ou de tirer parti de l’appel.  
  
 Utilisez le démarrage du traitement de raccordement de Notification  
 Il sera probablement plus facile de simplement fournir un nouveau pointeur à une fonction de raccordement fournie par l’utilisateur de notification qui reçoit les mêmes valeurs que l’assistance par défaut lors de la notification dliStartProcessing. À ce stade, la fonction de raccordement peut devenir la nouvelle fonction d’assistance, comme un retour réussi à l’assistance par défaut ignore tout traitement supplémentaire dans l’assistance par défaut.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge de l’éditeur de liens pour les DLL à chargement différé](../../build/reference/linker-support-for-delay-loaded-dlls.md)