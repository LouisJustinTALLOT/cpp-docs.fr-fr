---
title: Administrateur ODBC
ms.date: 11/04/2016
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
ms.openlocfilehash: 5e83657462952be12a6a2d086aa2419093e06d0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454792"
---
# <a name="odbc-administrator"></a>Administrateur ODBC

L’administrateur ODBC enregistre et configure le [des sources de données](../../data/odbc/data-source-odbc.md) auxquels vous avez localement ou sur un réseau. Les Assistants utilisent les informations fournies par l’administrateur ODBC pour créer du code dans vos applications qui se connecte vos utilisateurs aux sources de données.

Pour configurer une source de données ODBC à utiliser avec les classes ODBC MFC ou les classes de données Access objet DAO (MFC), vous devez d’abord inscrire et configurer la source de données. Utilisez l’administrateur ODBC pour ajouter et supprimer des sources de données. Selon le pilote ODBC, vous pouvez également créer de nouvelles sources de données.

L’administrateur ODBC est installé pendant l’installation. Si vous avez choisi **personnalisé** Installation et vous n’avez pas sélectionné de tous les pilotes ODBC dans le **les Options de base de données** boîte de dialogue, vous devez exécuter le programme d’installation pour installer les fichiers nécessaires.

Pendant l’installation, vous sélectionnez les pilotes ODBC que vous souhaitez installer. Vous pouvez installer ultérieurement des pilotes supplémentaires fournis avec Visual C++ à l’aide du programme d’installation de Visual C++.

Si vous souhaitez installer les pilotes ODBC ne sont pas fournis avec Visual C++, vous devez exécuter le programme d’installation du pilote.

#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>Pour installer les pilotes ODBC fournis avec Visual C++

1. Exécutez le programme d’installation à partir du CD-ROM Visual C++.

   L’ouverture est de boîte de dialogue dans le programme d’installation s’affiche.

1. Cliquez sur **suivant** sur chaque boîte de dialogue jusqu'à ce que vous atteigniez le **Options d’Installation** boîte de dialogue. Sélectionnez **personnalisé**, puis cliquez sur **suivant**.

1. Désactivez toutes les cases à cocher dans la **d’installation de Microsoft Visual C++** boîte de dialogue à l’exception la **les Options de base de données** case à cocher, puis cliquez sur **détails** pour afficher la **Les Options de base de données** boîte de dialogue.

1. Effacer la **Microsoft Data Access Objects** case à cocher, sélectionnez le **pilotes ODBC Microsoft** case à cocher, puis cliquez sur **détails**.

   Le **pilotes ODBC Microsoft** boîte de dialogue s’affiche.

1. Sélectionnez les pilotes que vous souhaitez installer, puis cliquez sur **OK** à deux reprises.

1. Cliquez sur **suivant** sur les boîtes de dialogue restantes pour commencer l’installation. Le programme d’installation vous avertit lorsque l’installation est terminée.

Lorsque les pilotes sont installés, vous pouvez configurer la source de données à l’aide de l’administrateur ODBC. Vous trouverez l’icône ODBC dans le panneau de configuration.

## <a name="see-also"></a>Voir aussi

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Source de données (ODBC)](../../data/odbc/data-source-odbc.md)