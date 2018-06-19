---
title: Fichiers d’entrée LIB | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 140a0f1d9ef6fdb3ca5e6d6977804684c88af1fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371965"
---
# <a name="lib-input-files"></a>Fichiers d'entrée LIB
Les fichiers d’entrée attendus par LIB dépendent du mode dans lequel il est utilisé, comme indiqué dans le tableau suivant.  
  
|Mode|Entrée|  
|----------|-----------|  
|Par défaut (création ou modification d’une bibliothèque)|Objets (.obj) fichiers, COFF bibliothèques (.lib), fichiers objets (.obj) de Format OMF (Object Model) 32 bits|  
|Extraction d’un membre avec /EXTRACT|Bibliothèque COFF (.lib)|  
|Création d’une exportation de fichier et de bibliothèque avec /DEF d’importation|Fichier de définition de module (.def), fichiers objets (.obj) COFF, des bibliothèques (.lib) COFF, les fichiers objets (.obj) OMF 32 bits|  
  
> [!NOTE]
>  Bibliothèques OMF créés par la version 16 bits de LIB ne peut pas être utilisés comme entrée pour la version 32 bits de LIB.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de LIB](../../build/reference/overview-of-lib.md)