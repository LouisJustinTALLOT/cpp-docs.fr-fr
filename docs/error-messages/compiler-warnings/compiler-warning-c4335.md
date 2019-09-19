---
title: Avertissement du compilateur C4335
ms.date: 11/04/2016
f1_keywords:
- C4335
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
ms.openlocfilehash: d44a1ae5354e8d22e41694f4d6df42ad22c3986d
ms.sourcegitcommit: 76cc69b482ada8ebf0837e8cdfd4459661f996dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127164"
---
# <a name="compiler-warning-c4335"></a>Avertissement du compilateur C4335

Format de fichier Mac détecté : convertissez le fichier source au format DOS ou UNIX

Le caractère de fin de ligne de la première ligne d’un fichier source est de type Macintosh (' \r') par opposition à UNIX (' \n') ou DOS (' \r\n').

Cet avertissement est toujours émis en tant qu’erreur.  Pour plus d’informations sur la façon de désactiver cet avertissement, consultez pragma [Warning](../../preprocessor/warning.md) .  En outre, cet avertissement n’est émis qu’une seule fois par module (compiland). Par conséquent, si plusieurs `#include` directives spécifient des fichiers au format Macintosh, C4335 ne sera émis qu’une seule fois.

L’une des méthodes permettant de générer des fichiers au format Macintosh est d’utiliser les **options d’enregistrement avancées** (dans le menu **fichier** ) dans Visual Studio.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4335.

```
// C4335 expected
#include "c4335.h"   // assume both include files are in Macintosh format
#include "c4335_2.h"
```
