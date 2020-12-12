---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4037'
title: Avertissement des outils Éditeur de liens LNK4037
ms.date: 10/04/2017
f1_keywords:
- LNK4037
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
ms.openlocfilehash: 78fd5ed9f8e2f82221b64053607846f1b8abc00a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331948"
---
# <a name="linker-tools-warning-lnk4037"></a>Avertissement des outils Éditeur de liens LNK4037

>'*symbol*'n’existe pas ; pas

Le *symbole* de nom décoré n’a pas pu être trié à l’aide de l’option [/Order](../../build/reference/order-put-functions-in-order.md) , car il est introuvable dans le programme. Vérifiez la spécification du *symbole* dans le fichier de réponse de commande. Pour plus d’informations, consultez l’option de l’éditeur de liens [/Order (mettre les fonctions dans l’ordre)](../../build/reference/order-put-functions-in-order.md) .

> [!NOTE]
> LINK ne peut pas trier les fonctions statiques, car les noms de fonctions statiques ne sont pas des noms de symboles publics. Quand **/Order** est spécifié, cet avertissement de l’éditeur de liens est généré pour chaque symbole dans le fichier de réponse de l’ordre qui est soit static, soit introuvable.
