---
title: Avertissement du compilateur C4335 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4335
dev_langs:
- C++
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2b28909d0c4b663fffeacbec58ad694131bb008
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036577"
---
# <a name="compiler-warning-c4335"></a>Avertissement du compilateur C4335

Format de fichier Mac détecté : convertissez le fichier source au format DOS ou UNIX

Le caractère de fin de ligne de la première ligne d’un fichier source est de style Macintosh ('\r') par opposition à UNIX ('\n') ou à MS-DOS (« \r\n »).

Cet avertissement est toujours émis en tant qu’erreur.  Consultez [avertissement](../../preprocessor/warning.md) pragma pour plus d’informations sur la façon de désactiver cet avertissement.  En outre, cet avertissement est émis uniquement une fois par compiland. Par conséquent, s’il existe plusieurs `#include` directives qui spécifient les fichiers au format Macintosh, C4335 seront émis une seule fois.

La première consiste à générer des fichiers au format Macintosh à l’aide de la **Options d’enregistrement avancées** (sur le **fichier** menu) dans Visual Studio.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4335.

```
// C4335 expected
#include "c4335.h"   // assume both include files are in Macintosh format
#include "c4335_2.h"
```