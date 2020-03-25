---
title: Erreur BSCMAKE BK1513
ms.date: 11/04/2016
f1_keywords:
- BK1513
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
ms.openlocfilehash: 3a16163f33814be18a67833995362ee9b13d8118
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197637"
---
# <a name="bscmake-error-bk1513"></a>Erreur BSCMAKE BK1513

une mise à jour non incrémentielle nécessite tous les fichiers .SBR

BSCMAKE ne peut pas générer un nouveau fichier d'informations de consultation (.bsc), car un ou plusieurs fichiers .sbr sont tronqués. Pour rechercher les noms des fichiers. sbr tronqués, lisez les avertissements [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) qui accompagnent cette erreur.

BSCMAKE peut mettre à jour un fichier .bsc avec un fichier .sbr tronqué, mais ne peut pas en générer un nouveau. BSCMAKE peut générer un nouveau fichier .bsc dans les cas suivants :

- Fichier .bsc manquant.

- Nom de fichier incorrect spécifié pour un fichier .bsc.

- Fichier .bsc endommagé.

Pour résoudre ce problème, supprimez les fichiers .sbr tronqués et procédez à une régénération, ou nettoyez la solution et procédez à une régénération. (Dans l’IDE, choisissez **générer**, **nettoyer la solution**, puis choisissez **générer**, **régénérer la solution**.)
