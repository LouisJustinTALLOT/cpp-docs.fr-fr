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
ms.openlocfilehash: 719ff1a87f3f1afc19cf38736c0059c46a8a9bdc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110872"
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