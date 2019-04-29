---
title: Erreur BSCMAKE BK1513
ms.date: 11/04/2016
f1_keywords:
- BK1513
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
ms.openlocfilehash: c02e9b47b3d32e4d21914188b96913d6dff03127
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279291"
---
# <a name="bscmake-error-bk1513"></a>Erreur BSCMAKE BK1513

une mise à jour non incrémentielle nécessite tous les fichiers .SBR

BSCMAKE ne peut pas générer un nouveau fichier d'informations de consultation (.bsc), car un ou plusieurs fichiers .sbr sont tronqués. Pour rechercher les noms des fichiers .sbr tronqués, lisez le [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) avertissements qui accompagnent cette erreur.

BSCMAKE peut mettre à jour un fichier .bsc avec un fichier .sbr tronqué, mais ne peut pas en générer un nouveau. BSCMAKE peut générer un nouveau fichier .bsc dans les cas suivants :

- Fichier .bsc manquant.

- Nom de fichier incorrect spécifié pour un fichier .bsc.

- Fichier .bsc endommagé.

Pour résoudre ce problème, supprimez les fichiers .sbr tronqués et procédez à une régénération, ou nettoyez la solution et procédez à une régénération. (Dans l’IDE, choisissez **Build**, **nettoyer la Solution**, puis choisissez **Build**, **régénérer la Solution**.)