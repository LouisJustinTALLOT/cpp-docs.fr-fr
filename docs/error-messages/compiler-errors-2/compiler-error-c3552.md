---
title: Erreur du compilateur C3552
ms.date: 11/04/2016
f1_keywords:
- C3552
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
ms.openlocfilehash: d2d3a60fcd4a26238cd6cf330f47b48c5b3198ad
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230829"
---
# <a name="compiler-error-c3552"></a>Erreur du compilateur C3552

'typename' : un type de retour spécifié à la fin ne peut pas contenir 'auto'

Si vous utilisez le **`auto`** mot clé en tant qu’espace réservé pour le type de retour d’une fonction, vous devez fournir un type de retour spécifié à la fin. Toutefois, vous ne pouvez pas utiliser un autre **`auto`** mot clé pour spécifier le type de retour spécifié à la fin. Par exemple, le fragment de code suivant génère l’erreur C3552.

`auto myFunction->auto; // C3552`
