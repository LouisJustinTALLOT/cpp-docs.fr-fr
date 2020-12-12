---
description: 'En savoir plus sur : erreur du compilateur C3552'
title: Erreur du compilateur C3552
ms.date: 11/04/2016
f1_keywords:
- C3552
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
ms.openlocfilehash: aca1474f53c8ac1a8257b23d0042550b76b3c0e8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223254"
---
# <a name="compiler-error-c3552"></a>Erreur du compilateur C3552

'typename' : un type de retour spécifié à la fin ne peut pas contenir 'auto'

Si vous utilisez le **`auto`** mot clé en tant qu’espace réservé pour le type de retour d’une fonction, vous devez fournir un type de retour spécifié à la fin. Toutefois, vous ne pouvez pas utiliser un autre **`auto`** mot clé pour spécifier le type de retour spécifié à la fin. Par exemple, le fragment de code suivant génère l’erreur C3552.

`auto myFunction->auto; // C3552`
