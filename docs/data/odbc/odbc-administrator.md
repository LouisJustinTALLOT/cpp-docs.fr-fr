---
title: Administrateur ODBC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- installing ODBC
- ODBC data sources [C++], ODBC Administrator
- ODBC drivers [C++], installing
- ODBC [C++], ODBC Administrator
- Administrator in ODBC
- administration ODBC Administrator
- ODBC Administrator [C++]
- drivers [C++], ODBC
ms.assetid: b8652790-3437-4e7d-bc83-6ea6981f008b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 55b214ba3513f95533e3892fb93ad9298c44415d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090193"
---
# <a name="odbc-administrator"></a>Administrateur ODBC
L’administrateur ODBC enregistre et configure le [des sources de données](../../data/odbc/data-source-odbc.md) disponibles localement ou sur un réseau. Les Assistants utilisent les informations fournies par l’administrateur ODBC pour créer du code dans vos applications qui connecte vos utilisateurs aux sources de données.  
  
 Pour configurer une source de données ODBC pour une utilisation avec les classes ODBC MFC ou les classes de données Access objet DAO (MFC), vous devez tout d’abord inscrire et configurer la source de données. Utilisez l’administrateur ODBC pour ajouter et supprimer des sources de données. Selon le pilote ODBC, vous pouvez également créer de nouvelles sources de données.  
  
 L’administrateur ODBC est installé pendant l’installation. Si vous avez choisi **personnalisé** Installation et vous n’avez pas sélectionné de tous les pilotes ODBC dans le **les Options de base de données** boîte de dialogue, vous devez exécuter le programme d’installation pour installer les fichiers nécessaires.  
  
 Pendant l’installation, vous sélectionnez les pilotes ODBC que vous souhaitez installer. Vous pouvez installer ultérieurement des pilotes supplémentaires fournis avec Visual C++ à l’aide du programme d’installation de Visual C++.  
  
 Si vous souhaitez installer les pilotes ODBC ne sont pas fournis avec Visual C++, vous devez exécuter le programme d’installation du pilote.  
  
#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>Pour installer les pilotes ODBC fournis avec Visual C++  
  
1.  Exécutez le programme d’installation à partir du CD-ROM Visual C++.  
  
     L’ouverture est de boîte de dialogue du programme d’installation s’affiche.  
  
2.  Cliquez sur **suivant** sur chaque boîte de dialogue jusqu'à ce que vous atteigniez le **Options d’Installation** boîte de dialogue. Sélectionnez **personnalisé**, puis cliquez sur `Next`.  
  
3.  Désactivez toutes les cases à cocher dans la **d’installation de Microsoft Visual C++** boîte de dialogue à l’exception de la **les Options de base de données** case à cocher, puis cliquez sur **détails** pour afficher la **Les Options de base de données** boîte de dialogue.  
  
4.  Désactivez le **Microsoft Data Access Objects** case à cocher, sélectionnez le **pilotes ODBC Microsoft** case à cocher, puis cliquez sur **détails**.  
  
     Le **pilotes ODBC Microsoft** boîte de dialogue s’affiche.  
  
5.  Sélectionnez les pilotes que vous souhaitez installer, puis cliquez sur **OK** à deux reprises.  
  
6.  Cliquez sur **suivant** sur les boîtes de dialogue restantes pour commencer l’installation. Le programme d’installation vous informe lorsque l’installation est terminée.  
  
 Lorsque les pilotes sont installés, vous pouvez configurer la source de données à l’aide de l’administrateur ODBC. Vous trouverez l’icône ODBC dans le panneau de configuration.  
  
## <a name="see-also"></a>Voir aussi  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Source de données (ODBC)](../../data/odbc/data-source-odbc.md)