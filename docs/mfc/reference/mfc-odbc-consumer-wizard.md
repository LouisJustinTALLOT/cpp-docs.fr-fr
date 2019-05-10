---
title: Consommateur ODBC MFC (Assistant)
ms.date: 05/09/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: 20357646bbb7aa4fe00db43d8e77f9bf0b95c9b5
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525364"
---
# <a name="mfc-odbc-consumer-wizard"></a>Consommateur ODBC MFC (Assistant)

::: moniker range="vs-2019"

Cet Assistant n’est pas disponible dans Visual Studio 2019 et versions ultérieures.

::: moniker-end

::: moniker range="vs-2017"

Cet Assistant définit une classe de jeu d’enregistrements ODBC et les liaisons de données nécessaire pour accéder à la source de données spécifié.

## <a name="uielement-list"></a>Liste des éléments d’interface

- **Source de données**

  Le **Source de données** bouton vous permet de définir la source de données spécifié à l’aide du pilote ODBC spécifié. Pour plus d’informations sur les fichiers de source de données (DSN), consultez [les Sources de données de fichier](/sql/odbc/reference/file-data-sources) dans le SDK ODBC.

  Le **sélectionner une Source de données** boîte de dialogue comporte deux onglets :

  - **Fichier Source de données** onglet :

     Le **Regarder dans** zone spécifie le répertoire dans lequel sélectionner les fichiers à utiliser comme sources de données. La valeur par défaut est \Program Files\ODBC\Data Sources. Les sources de données de fichiers existants (fichiers .dsn) s’affichent dans la zone de liste principale. Vous pouvez configurer les sources de données avant l’heure à l’aide de la **fichier DSN** onglet sur le [administrateur de sources de données ODBC](/sql/odbc/admin/odbc-data-source-administrator), ou créer de nouveaux à l’aide de cette boîte de dialogue.

     Pour créer une nouvelle source de données de fichier à partir de cette boîte de dialogue, cliquez sur `New` pour spécifier un nom de source de données ; la **créer une nouvelle Source de données** boîte de dialogue s’affiche. Dans le **créer une nouvelle Source de données** boîte de dialogue, sélectionnez un pilote approprié puis cliquez sur `Next`; cliquez sur **Parcourir**, puis sélectionnez le nom du fichier à utiliser comme source de données (vous devez sélectionner « Tous les fichiers » pour afficher les fichiers non DSN, tels que les fichiers .xls) ; Cliquez sur `Next`, puis cliquez sur **Terminer**. (Si vous avez sélectionné un fichier non DSN, vous obtiendrez une boîte de dialogue de spécifiques au pilote, tels que « Installation ODBC pour Microsoft Excel, » qui convertira le fichier à une source de données.)

     > [!NOTE]
     > Vous pouvez également créer une nouvelle source de données de fichier au préalable à l’aide de l’administrateur de sources de données ODBC. À partir de la **Démarrer** menu, sélectionnez **paramètres**, **le panneau de configuration**, **outils d’administration**, **deSourcesdedonnées(ODBC)**, puis **administrateur de sources de données ODBC**.

     Le **nom DSN** boîte vous permet de spécifier un nom pour la source de données de fichier. Vous devez vous assurer que le nom de source de données se termine avec l’extension de fichier approprié, tel que .xls pour les fichiers Excel ou .mdb pour accéder aux fichiers.

     Pour plus d’informations sur les sources de données, consultez [les Sources de données de fichier](/sql/odbc/reference/file-data-sources) dans le SDK ODBC.

  - **Source de données de l’ordinateur** onglet :

     Cet onglet répertorie les sources système et données utilisateur. Sources de données utilisateur sont spécifiques à un utilisateur sur cet ordinateur. Sources de données système peuvent être utilisés par tous les utilisateurs sur cet ordinateur ou d’un service système. Consultez [Machine des Sources de données](/sql/odbc/reference/machine-data-sources) dans le Kit de développement logiciel ODBC

     Pour plus d’informations sur les sources de données ODBC, consultez [des Sources de données](/sql/odbc/reference/data-sources) dans le SDK ODBC.

  Cliquez sur **OK** se termine. Le **sélectionner un objet de base de données** boîte de dialogue s’affiche. À partir de cette boîte de dialogue, sélectionnez la table ou afficher que le consommateur doit utiliser. Notez que vous pouvez sélectionner plusieurs vues et tables en maintenant la touche CTRL tout en cliquant sur les éléments. Cliquez sur **OK** se termine.

- **Classe**

      The name of the consumer class, based by default on the name of the file or machine data source that you selected.

- **Fichier .h**

   Le nom du consommateur classe fichier d’en-tête, par défaut est basé sur le nom de la source de données de fichier ou de la machine que vous avez sélectionné.

- **Fichier .cpp**

   Le nom du consommateur classe fichier d’implémentation, par défaut est basé sur le nom de la source de données de fichier ou de la machine que vous avez sélectionné.

- **Type**

   Spécifie si le recordset est une feuille de réponse dynamique (par défaut) ou un instantané.

   - **Feuille de réponse dynamique**: Spécifie que le jeu d’enregistrements est une feuille de réponse dynamique. Un jeu de données est le résultat d’une requête qui fournit une vue indexée dans les données de la base de données interrogée. Feuille de réponse dynamique met en cache qu’un index intégral pour les données d’origine et de gagner ainsi offre un performances sur un instantané. L’index pointe directement vers chaque enregistrement trouvé à la suite d’une requête et indique si un enregistrement est supprimé. Vous avez également accès aux informations mises à jour dans les enregistrements interrogées. Il s'agit de la valeur par défaut.

   - **Instantané**: Spécifie que le jeu d’enregistrements est un instantané. Un instantané est le résultat d’une requête et est une vue dans une base de données à un point dans le temps. Tous les enregistrements trouvés à la suite de la requête sont mis en cache, vous ne voyez pas les modifications apportées aux enregistrements d’origine.

- **Lier toutes les colonnes**

   Spécifie si toutes les colonnes dans la table sélectionnée sont liées. Si vous activez cette case (valeur par défaut), toutes les colonnes sont liées ; Si vous ne sélectionnez pas cette case, aucune colonne n’est liés, et vous devez les lier manuellement dans la classe de jeu d’enregistrements.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[MFC ODBC, consommation](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)
