---
title: Avertissement LNK4221 des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4221
dev_langs:
- C++
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8906c4308b8586d5b1312739921f58063e820deb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301006"
---
# <a name="linker-tools-warning-lnk4221"></a>Avertissement des outils Éditeur de liens LNK4221
Ce fichier objet ne définit pas de symboles publics jusqu’ici non définis, afin qu’il ne sera pas être utilisé par l’opération de liaison qui utilise cette bibliothèque  
  
 Envisagez d’extraits de deux code suivants.  
  
```  
// a.cpp  
#include <atlbase.h>  
```  
  
```  
// b.cpp  
#include <atlbase.h>  
int function()  
{  
   return 0;  
}  
  
```  
  
 Pour compiler les fichiers et créer deux fichiers objets, exécutez **cl /c a.cpp b.cpp** à une invite de commandes. Si vous liez les fichiers objets en exécutant **lien/lib /out:test.lib a.obj b.obj**, vous recevrez l’avertissement LNK4221. Si vous liez les objets en exécutant **lien/lib /out:test.lib b.obj a.obj**, un avertissement ne s’affiche pas.  
  
 Aucun avertissement n’est émis dans le deuxième scénario, car l’éditeur de liens fonctionne de façon dernier entré premier sorti (LIFO). Dans le premier scénario, b.obj est traité avant a.obj, et a.obj n’a aucun nouveau symbole à ajouter. En demandant à l’éditeur de liens de traiter d’abord a.obj, vous pouvez éviter l’avertissement.  
  
 Une cause courante de cette erreur est lorsque les deux fichiers sources spécifient l’option [/Yc (créer un en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md) avec le même nom de fichier d’en-tête spécifié dans le **d’un en-tête précompilé** champ. Une cause courante de ce problème est liée à stdafx.h dans la mesure où, par défaut, stdafx.cpp inclut stdafx.h et n’ajoute pas de nouveaux symboles. Si un autre fichier source inclut stdafx.h avec **/Yc** et le fichier .obj associé est traité avant stdafx.obj, l’éditeur de liens lèvera l’avertissement LNK4221.  
  
 Une façon de résoudre ce problème consiste à vous assurer que chaque en-tête précompilé, il n'existe qu’un seul fichier source inclut avec **/Yc**. Tous les autres fichiers sources doivent utiliser des en-têtes précompilés. Pour plus d’informations sur la façon de modifier ce paramètre, consultez [/Yu (utiliser un en-tête précompilé)](../../build/reference/yu-use-precompiled-header-file.md).