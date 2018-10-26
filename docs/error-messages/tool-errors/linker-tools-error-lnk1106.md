---
title: Erreur des LNK1106 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1106
dev_langs:
- C++
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce6a8b2ef9ac807e48cff42186453666cebda5ee
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055982"
---
# <a name="linker-tools-error-lnk1106"></a>Erreur des outils Éditeur de liens LNK1106

fichier non valide ou disque plein : Impossible de rechercher à l’emplacement

L’outil ne peut pas lire ou écrire dans `location` dans un fichier mappé en mémoire.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Disque plein.

   Libérer de l’espace et le lier à nouveau.

1. Essayez de lier un réseau.

   Certains réseaux ne prennent pas entièrement en charge les fichiers mappés en mémoire utilisés par l’éditeur de liens. Essayer la liaison sur votre disque local.

1. Bloc défectueux sur votre disque.

   Bien que le système d’exploitation et le matériel de disque doivent avoir a détecté une telle erreur, vous souhaiterez exécuter un programme de vérification du disque.

1. Espace du tas insuffisant.

   Consultez [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) pour plus d’informations.