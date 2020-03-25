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
ms.openlocfilehash: 9e88492919eac80a4f3db2f94202d49011aa69de
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213163"
---
# <a name="odbc-administrator"></a>Administrateur ODBC

L’administrateur ODBC inscrit et configure les [sources de données](../../data/odbc/data-source-odbc.md) disponibles localement ou sur un réseau. Les assistants utilisent les informations fournies par l’administrateur ODBC pour créer du code dans vos applications qui connectent vos utilisateurs aux sources de données.

Pour configurer une source de données ODBC pour une utilisation avec les classes ODBC MFC ou les classes DAO (Data Access Object) MFC, vous devez d’abord inscrire et configurer la source de données. Utilisez l’administrateur ODBC pour ajouter et supprimer des sources de données. En fonction du pilote ODBC, vous pouvez également créer des sources de données.

L’administrateur ODBC est installé lors de l’installation. Si vous avez choisi l’installation **personnalisée** et que vous n’avez pas sélectionné de pilotes ODBC dans la boîte **de dialogue Options de base de données** , vous devez réexécuter le programme d’installation pour installer les fichiers nécessaires.

Pendant l’installation, vous sélectionnez les pilotes ODBC que vous souhaitez installer. Vous pouvez installer ultérieurement des pilotes supplémentaires fournis avec Visual C++ à l’aide C++ du programme d’installation de Visual.

Si vous souhaitez installer des pilotes ODBC qui ne sont pas fournis avec C++Visual, vous devez exécuter le programme d’installation qui accompagne le pilote.

#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>Pour installer les pilotes ODBC fournis avec VisualC++

1. Exécutez le programme d’installation C++ à partir de votre CD de distribution visuel.

   La boîte de dialogue d’ouverture du programme d’installation s’affiche.

1. Cliquez sur **suivant** dans chaque boîte de dialogue jusqu’à ce que vous atteigniez la boîte de dialogue **options d’installation** . Sélectionnez **personnalisé**, puis cliquez sur **suivant**.

1. Désactivez toutes les cases à cocher dans la boîte de dialogue  **C++ installation de Microsoft Visual** , à l’exception des **options de base de données** , puis cliquez sur **Détails** pour afficher la boîte **de dialogue Options de base de données** .

1. Désactivez la case à cocher **Microsoft Data Access Objects** , activez la case à cocher **pilotes ODBC Microsoft** , puis cliquez sur **Détails**.

   La boîte de dialogue **pilotes Microsoft ODBC** s’affiche.

1. Sélectionnez les pilotes que vous souhaitez installer, puis cliquez deux fois sur **OK** .

1. Cliquez sur **suivant** dans les boîtes de dialogue restantes pour commencer l’installation. Le programme d’installation vous avertit lorsque l’installation est terminée.

Lorsque les pilotes sont installés, vous pouvez configurer la source de données à l’aide de l’administrateur ODBC. Vous trouverez l’icône ODBC dans le panneau de configuration.

## <a name="see-also"></a>Voir aussi

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Source de données (ODBC)](../../data/odbc/data-source-odbc.md)
