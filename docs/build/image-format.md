---
title: Format d'image
ms.date: 11/04/2016
ms.assetid: 3ca3654b-42fe-4253-9f2e-723644041aa0
ms.openlocfilehash: 71456af35960114ab64b076ebb9c0f9102613744
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509939"
---
# <a name="image-format"></a>Format d'image

Le format d’image exécutable est PE32 +. Les images exécutables (DLL et exe) sont limitées à une taille maximale de 2 gigaoctets, afin de l’adressage relatif avec un déplacement 32 bits peut être utilisé pour traiter les données d’image statique. Ces données incluent la table des adresses d’importation, les constantes de chaîne, les données globales statiques et ainsi de suite.

## <a name="see-also"></a>Voir aussi

[Conventions des logiciels x64](../build/x64-software-conventions.md)