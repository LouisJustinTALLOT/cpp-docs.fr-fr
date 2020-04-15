---
title: Consommateur ODBC MFC (Assistant)
ms.date: 08/29/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: 45087434c0093f99383096761d58a8029c9d5009
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373025"
---
# <a name="mfc-odbc-consumer-wizard"></a>Consommateur ODBC MFC (Assistant)

::: moniker range="vs-2019"

Cet Assistant n’est pas disponible dans Visual Studio 2019 et ultérieur.

::: moniker-end

::: moniker range="<=vs-2017"

Cet assistant met en place une classe de documents ODBC et les liaisons de données nécessaires pour accéder à la source de données spécifiée.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

- **Source de données**

  Le bouton **Source de données** vous permet de configurer la source de données spécifiée à l’aide du pilote ODBC spécifié. Pour plus d’informations sur les fichiers sources de données (DSN), voir [Les sources de données](/sql/odbc/reference/file-data-sources) des fichiers dans le SDK ODBC.

  La boîte de dialogue **Select Data Source** comporte deux onglets :

  - **Onglet Source de données de fichier** :

     Le **Look in** box spécifie l’annuaire dans lequel sélectionner les fichiers à utiliser comme sources de données. La valeur par défaut est le système de fichiers de programme, les fichiers communs, les sources de données ODBC. Les sources de données de fichiers existantes (.fichiers dsn) apparaissent dans la case de liste principale. Vous pouvez soit configurer les sources de données à l’avance à l’aide de **l’onglet DSN de fichier** sur l’administrateur [de source de données ODBC,](/sql/odbc/admin/odbc-data-source-administrator)soit en créer de nouvelles à l’aide de cette boîte de dialogue.

     Pour créer une nouvelle source de données `New` de fichiers à partir de cette boîte de dialogue, cliquez pour spécifier un nom DSN ; la boîte de dialogue **Create New Data Source** apparaît. Dans la boîte de dialogue Create New Data `Next` **Source,** sélectionnez un pilote approprié et cliquez sur ; cliquez **sur Parcourir**et sélectionnez le nom du fichier à utiliser comme source de données (vous devez sélectionner "Tous les fichiers" pour afficher les fichiers non-DSN, tels que les fichiers .xls); cliquez `Next`, puis cliquez sur **Finition**. (Si vous avez sélectionné un fichier non-DSN, vous obtiendrez une boîte de dialogue spécifique au conducteur, comme "ODBC Microsoft Excel Setup", qui convertira le fichier en DSN.)

     > [!NOTE]
     > Vous pouvez également créer une nouvelle source de données de fichiers à l’avance à l’aide de l’administrateur de source de données ODBC. Du menu **Démarrer,** sélectionnez **Paramètres,** **Panneau de contrôle**, Outils **administratifs**, **Sources de données (ODBC)**, puis **ODBC Data Source Administrator**.

     La boîte **nom DSN** vous permet de spécifier un nom pour la source de données de fichier. Vous devez vous assurer que le nom DSN se termine par l’extension de fichier appropriée, comme .xls pour les fichiers Excel ou .mdb pour les fichiers d’accès.

     Pour plus d’informations sur les DSN, voir [Les sources de données de fichiers](/sql/odbc/reference/file-data-sources) dans le SDK ODBC.

  - **Onglet Source de données de machine** :

     Cet onglet répertorie les sources de système et de DONNÉES utilisateur. Les sources de données utilisateur sont spécifiques à un utilisateur sur cette machine. Les sources de données système peuvent être utilisées par tous les utilisateurs sur cette machine ou sur un service à l’échelle du système. Voir [Les sources de données des machines](/sql/odbc/reference/machine-data-sources) dans le SDK ODBC

     Pour plus d’informations sur les sources de données ODBC, voir [Sources de données](/sql/odbc/reference/data-sources) dans le SDK ODBC.

  Cliquez sur **OK** pour terminer. La boîte de dialogue **Sélectionner l’objet de base de données** s’affiche. De cette boîte de dialogue, sélectionnez la table ou la vue que le consommateur utilisera. Notez que vous pouvez sélectionner plusieurs vues et tableaux en tenant la clé de contrôle tout en cliquant sur les éléments. Cliquez sur **OK** pour terminer.

- **Classe**

   Le nom de la classe de consommateurs, basé par défaut sur le nom du fichier ou de la source de données de la machine que vous avez sélectionné.

- **Fichier .h**

   Le nom du fichier d’en-tête de la classe grand public, basé par défaut sur le nom du fichier ou de la source de données de la machine que vous avez sélectionné.

- **Fichier .cpp**

   Le nom du fichier de mise en œuvre de la classe des consommateurs, basé par défaut sur le nom du fichier ou de la source de données de la machine que vous avez sélectionné.

- **Type**

   Précise si le jeu d’enregistrement est un dynaset (par défaut) ou un instantané.

  - **Dynaset**: Précise que le recordet est un dynaset. Un dynaset est le résultat d’une requête qui fournit une vue indexée dans les données de la base de données demandée. Un dynaset cache seulement un index intégral aux données originales et offre ainsi un gain de performance sur un instantané. L’index indique directement chaque enregistrement trouvé à la suite d’une requête et indique si un enregistrement est supprimé. Vous avez également accès à des informations mises à jour dans les dossiers interrogés. Il s’agit de la valeur par défaut.

  - **Instantané**: Spécifie que le livre est un instantané. Un instantané est le résultat d’une requête et est une vue dans une base de données à un moment donné dans le temps. Tous les enregistrements trouvés à la suite de la requête sont mis en cache, de sorte que vous ne voyez pas de modifications aux enregistrements originaux.

- **Lier toutes les colonnes**

   Précise si toutes les colonnes du tableau sélectionné sont liées. Si vous sélectionnez cette boîte (par défaut), toutes les colonnes sont liées; si vous ne sélectionnez pas cette boîte, aucune colonne n’est liée, et vous devez les lier manuellement dans la classe de recordet.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Consommation ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)
