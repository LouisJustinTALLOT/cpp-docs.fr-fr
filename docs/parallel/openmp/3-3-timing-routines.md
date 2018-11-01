---
title: 3.3 Routines de minutage
ms.date: 11/04/2016
ms.assetid: 21060d64-cbe8-4e38-8718-3a68d6a57be3
ms.openlocfilehash: 404e9e168c916b70c7cd32042822f290cd560e98
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630475"
---
# <a name="33-timing-routines"></a>3.3 Routines de minutage

Les fonctions décrites dans cette section prennent en charge un minuteur d’horloge portable :

- Le `omp_get_wtime` fonction retourne le temps horloge écoulé.

- Le `omp_get_wtick` fonction retourne les secondes entre les battements d’horloge successives.