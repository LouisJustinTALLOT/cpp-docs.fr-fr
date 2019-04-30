---
title: Avertissement des outils Éditeur de liens LNK4037
ms.date: 10/04/2017
f1_keywords:
- LNK4037
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
ms.openlocfilehash: 9a8121617e622fc12efe5bd26aac23faf2530f24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410302"
---
# <a name="linker-tools-warning-lnk4037"></a>Avertissement des outils Éditeur de liens LNK4037

>«*symbole*' n’existe pas ; ignoré

Le nom décoré *symbole* n’a pas pu être trié à l’aide de la [/Order](../../build/reference/order-put-functions-in-order.md) option, car il est introuvable dans le programme. Vérifiez la spécification de *symbole* dans le fichier de réponse de commande. Pour plus d’informations, consultez le [/ORDER (mettre les fonctions dans l’ordre)](../../build/reference/order-put-functions-in-order.md) option de l’éditeur de liens.

> [!NOTE]
> LIEN ne peut pas classer les fonctions statiques, car les noms de fonctions statiques ne sont pas des noms de symboles publics. Lorsque **/Order** est spécifié, l’éditeur de liens en cet avertissement est généré pour chaque symbole dans le fichier de réponse de commande qui est soit statique ou introuvable.