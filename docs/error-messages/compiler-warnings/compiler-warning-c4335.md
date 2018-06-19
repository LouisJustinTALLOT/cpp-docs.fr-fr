---
title: Avertissement du compilateur C4335 | Documents Microsoft
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
ms.openlocfilehash: adb8a7b484ce0946f385c3b2a8669ba1b5ccf0d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270507"
---
# <a name="compiler-warning-c4335"></a>Avertissement du compilateur C4335
Format de fichier Mac détecté : convertissez le fichier source au format DOS ou UNIX  
  
 Le caractère de fin de ligne de la première ligne d’un fichier source est de style Macintosh ('\r') par opposition à UNIX ('\n') ou à DOS ('\r\n').  
  
 Cet avertissement est toujours émis en tant qu’erreur.  Consultez [avertissement](../../preprocessor/warning.md) pragma pour plus d’informations sur la manière de désactiver cet avertissement.  En outre, cet avertissement est émis uniquement une fois par compiland. Par conséquent, s’il existe plusieurs `#include` directives qui spécifient des fichiers au format Macintosh, C4335 est générée qu’une seule fois.  
  
 Une façon de générer des fichiers au format Macintosh consiste à l’aide de la **Options d’enregistrement avancées** (sur le **fichier** menu) dans Visual Studio.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4335.  
  
```  
// C4335 expected  
#include "c4335.h"   // assume both include files are in Macintosh format  
#include "c4335_2.h"  
```