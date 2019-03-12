---
title: Compatibilité descendante
ms.date: 11/04/2016
f1_keywords:
- c.programs
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
ms.openlocfilehash: f672f0601a9d20a726f90963265d08ec212dedce
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744478"
---
# <a name="backward-compatibility"></a>Compatibilité descendante

Pour la compatibilité entre les versions de produit, la bibliothèque OLDNAMES.LIB mappe les anciens noms sur les nouveaux. Par exemple, `open` est mappé sur `_open`. Vous devez lier explicitement avec OLDNAMES.LIB uniquement lorsque vous compilez avec les combinaisons d’options de ligne de commande suivantes :

- `/Zl` (omettez le nom de la bibliothèque par défaut dans le fichier objet) et `/Ze` (par défaut - utilisez les extensions Microsoft)

- `/link` (contrôle d’éditeur de lien), `/NOD` (pas de recherche dans la bibliothèque par défaut) et `/Ze`

Pour plus d’informations sur les options de ligne de commande du compilateur, consultez l’article [Référence du compilateur](../build/reference/compiler-options.md).

## <a name="see-also"></a>Voir aussi

[Compatibilité](../c-runtime-library/compatibility.md)
