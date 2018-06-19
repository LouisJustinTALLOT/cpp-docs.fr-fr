---
title: Erreur irrécupérable C1854 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1854
dev_langs:
- C++
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e517832720e31bfae88e79ad879f1427b9c25a48
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230237"
---
# <a name="fatal-error-c1854"></a>Erreur irrécupérable C1854
  
> ne peut pas remplacer les informations obtenues lors de la création de l’en-tête précompilé du fichier objet : '*nom de fichier*'  
  
Vous avez spécifié le [/Yu (utiliser un en-tête précompilé)](../../build/reference/yu-use-precompiled-header-file.md) option après avoir spécifié le [/Yc (créer un en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md) option pour le même fichier.  
  
Pour résoudre ce problème, en général, ne définir qu’un seul fichier dans votre projet doit être compilé à l’aide de la **/Yc** option et définissez tous les autres fichiers à compiler à l’aide de la **/Yu** option. Pour plus d’informations sur l’utilisation de la **/Yc** option et la définir dans l’IDE de Visual Studio, consultez [/Yc (créer un en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md). Pour plus d’informations sur l’utilisation d’en-têtes précompilés, consultez [création de fichiers d’en-tête précompilés](../../build/reference/creating-precompiled-header-files.md).  
