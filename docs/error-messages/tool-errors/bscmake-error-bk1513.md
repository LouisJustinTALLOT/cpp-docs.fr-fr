---
title: Erreur BSCMAKE BK1513 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1513
dev_langs:
- C++
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f68f49ce11c95672abd40ecbaf1873a564a3912e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118802"
---
# <a name="bscmake-error-bk1513"></a>Erreur BSCMAKE BK1513

une mise à jour non incrémentielle nécessite tous les fichiers .SBR

BSCMAKE ne peut pas générer un nouveau fichier d'informations de consultation (.bsc), car un ou plusieurs fichiers .sbr sont tronqués. Pour rechercher les noms des fichiers .sbr tronqués, lisez le [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) avertissements qui accompagnent cette erreur.

BSCMAKE peut mettre à jour un fichier .bsc avec un fichier .sbr tronqué, mais ne peut pas en générer un nouveau. BSCMAKE peut générer un nouveau fichier .bsc dans les cas suivants :

- Fichier .bsc manquant.

- Nom de fichier incorrect spécifié pour un fichier .bsc.

- Fichier .bsc endommagé.

Pour résoudre ce problème, supprimez les fichiers .sbr tronqués et procédez à une régénération, ou nettoyez la solution et procédez à une régénération. (Dans l’IDE, choisissez **Build**, **nettoyer la Solution**, puis choisissez **Build**, **régénérer la Solution**.)