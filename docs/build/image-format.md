---
title: Format d’image | Microsoft Docs
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
ms.openlocfilehash: 0e69d1a7c62d4e9c52cc628f30f94c346d83647f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715414"
---
# <a name="image-format"></a>Format d'image

Le format d’image exécutable est PE32 +. Les images exécutables (DLL et exe) sont limitées à une taille maximale de 2 gigaoctets, afin de l’adressage relatif avec un déplacement 32 bits peut être utilisé pour traiter les données d’image statique. Ces données incluent la table des adresses d’importation, les constantes de chaîne, les données globales statiques et ainsi de suite.

## <a name="see-also"></a>Voir aussi

[Conventions des logiciels x64](../build/x64-software-conventions.md)