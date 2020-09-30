---
title: Backward Compatibility
description: Comment utiliser Microsoft OLDNAMES. Bibliothèque LIB pour mapper les noms de fonction à des fins de compatibilité descendante.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
ms.openlocfilehash: b09104a5cff4d8e4cc31f9cc4707e808988401d6
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590288"
---
# <a name="backward-compatibility"></a>Backward Compatibility

Pour la compatibilité entre les versions de produit, la bibliothèque OLDNAMES.LIB mappe les anciens noms sur les nouveaux. Par exemple, `open` est mappé sur `_open`. Vous devez lier explicitement avec OLDNAMES.LIB uniquement lorsque vous compilez avec les combinaisons d’options de ligne de commande suivantes :

- `/Zl` (omettez le nom de la bibliothèque par défaut dans le fichier objet) et `/Ze` (par défaut - utilisez les extensions Microsoft)

- `/link` (contrôle d’éditeur de lien), `/NOD` (pas de recherche dans la bibliothèque par défaut) et `/Ze`

Pour plus d’informations sur les options de ligne de commande du compilateur, consultez l’article [Référence du compilateur](../build/reference/compiler-options.md).

## <a name="see-also"></a>Voir aussi

[Compatibilité](../c-runtime-library/compatibility.md)
