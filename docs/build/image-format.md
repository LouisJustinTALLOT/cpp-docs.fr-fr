---
title: Format d’image | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 3ca3654b-42fe-4253-9f2e-723644041aa0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 356480333a62d998213726016f3940b318c218a0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367938"
---
# <a name="image-format"></a>Format d'image
Le format d’image exécutable est PE32 +. Images exécutables (DLL et exe) sont limitées à une taille maximale de 2 gigaoctets, pour l’adressage relatif avec un déplacement 32 bits peut être utilisée pour traiter les données d’image statique. Ces données incluent la table des adresses d’importation, les constantes de chaîne, les données globales statiques et ainsi de suite.  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions des logiciels x64](../build/x64-software-conventions.md)