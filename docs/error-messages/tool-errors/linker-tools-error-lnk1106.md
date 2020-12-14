---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1106'
title: Erreur des outils Éditeur de liens LNK1106
ms.date: 11/04/2016
f1_keywords:
- LNK1106
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
ms.openlocfilehash: 85f353b6424cdd9ad12a99b29fec4f6119472cdb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281403"
---
# <a name="linker-tools-error-lnk1106"></a>Erreur des outils Éditeur de liens LNK1106

fichier non valide ou disque plein : impossible de Rechercher l’emplacement

L’outil n’a pas pu lire ou écrire `location` dans un fichier mappé en mémoire.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Disque plein.

   Libérez de l’espace et liez à nouveau.

1. Tentative de liaison sur un réseau.

   Certains réseaux ne prennent pas entièrement en charge les fichiers mappés en mémoire utilisés par l’éditeur de liens. Essayez d’effectuer la liaison sur votre disque local.

1. Bloc incorrect sur votre disque.

   Même si le système d’exploitation et le matériel de disque doivent avoir détecté une telle erreur, vous pouvez exécuter un programme de vérification de disque.

1. Espace du tas insuffisant.

   Pour plus d’informations, consultez [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) .
