---
title: Consommateur ODBC MFC (Assistant)
ms.date: 08/29/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: c915408eede80c1564dacc88ab7b9354bd72fc11
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92918836"
---
# <a name="mfc-odbc-consumer-wizard"></a>Consommateur ODBC MFC (Assistant)

::: moniker range="msvc-160"

Cet Assistant n’est pas disponible dans Visual Studio 2019 et ultérieur.

::: moniker-end

::: moniker range="<=msvc-150"

Cet Assistant Configure une classe de Recordset ODBC et les liaisons de données nécessaires pour accéder à la source de données spécifiée.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

- **Source de données**

  Le bouton **source de données** vous permet de configurer la source de données spécifiée à l’aide du pilote ODBC spécifié. Pour plus d’informations sur les fichiers de source de données (DSN), consultez [sources de données de fichiers](/sql/odbc/reference/file-data-sources) dans le kit de développement logiciel (SDK) ODBC.

  La boîte de dialogue **Sélectionner une source de données** comporte deux onglets :

  - Onglet **source de données de fichier** :

     La zone **regarder dans** spécifie le répertoire dans lequel sélectionner les fichiers à utiliser comme sources de données. La valeur par défaut est \Program Files\Common Files\ODBC\Data Sources. Les sources de données de fichiers existantes (fichiers. DSN) s’affichent dans la zone de liste principale. Vous pouvez configurer les sources de données à l’avance à l’aide de l’onglet **fichier DSN** de l’administrateur de la [source de données ODBC](/sql/odbc/admin/odbc-data-source-administrator)ou en créer d’autres à l’aide de cette boîte de dialogue.

     Pour créer une source de données de fichier à partir de cette boîte de dialogue, cliquez sur `New` pour spécifier un nom de DSN ; la boîte de dialogue **créer une nouvelle source de données** s’affiche. Dans la boîte de dialogue **créer une nouvelle source de données** , sélectionnez un pilote approprié, cliquez `Next` sur **Parcourir** , puis sélectionnez le nom du fichier à utiliser comme source de données (vous devez sélectionner « tous les fichiers » pour afficher les fichiers non DSN, tels que les fichiers. xls); cliquez sur `Next` , puis sur **Terminer** . (Si vous avez sélectionné un fichier non DSN, vous obtiendrez une boîte de dialogue spécifique au pilote, telle que « installation ODBC pour Microsoft Excel », qui convertira le fichier en un nom de source de donnée.)

     > [!NOTE]
     > Vous pouvez également créer au préalable une nouvelle source de données de fichier à l’aide de l’administrateur de la source de données ODBC. Dans le menu **Démarrer** , sélectionnez **paramètres** , **panneau** de configuration, **Outils d’administration** , **sources de données (ODBC)** , puis **administrateur de source de données ODBC** .

     La zone **nom du DSN** vous permet de spécifier un nom pour la source de données de fichier. Vous devez vous assurer que le nom du DSN se termine par l’extension de fichier appropriée, par exemple. xls pour les fichiers Excel ou. mdb pour les fichiers Access.

     Pour plus d’informations sur les DSN, consultez [sources de données de fichiers](/sql/odbc/reference/file-data-sources) dans le kit de développement logiciel (SDK) ODBC.

  - Onglet **source de données** de l’ordinateur :

     Cet onglet répertorie les sources de données système et utilisateur. Les sources de données utilisateur sont spécifiques à un utilisateur sur cet ordinateur. Les sources de données système peuvent être utilisées par tous les utilisateurs sur cet ordinateur ou sur un service à l’échelle du système. Voir les [sources de données machine](/sql/odbc/reference/machine-data-sources) dans le kit de développement logiciel (SDK) ODBC

     Pour plus d’informations sur les sources de données ODBC, consultez [sources de données](/sql/odbc/reference/data-sources) dans le kit de développement logiciel (SDK) ODBC.

  Cliquez sur **OK** pour terminer. La boîte de dialogue **Sélectionner l’objet de base de données** s’affiche. Dans cette boîte de dialogue, sélectionnez la table ou la vue que le consommateur utilisera. Notez que vous pouvez sélectionner plusieurs vues et tables en maintenant la touche CTRL enfoncée tout en cliquant sur les éléments. Cliquez sur **OK** pour terminer.

- **Classe**

   Nom de la classe de consommateur, basé par défaut sur le nom de la source de données du fichier ou de l’ordinateur que vous avez sélectionné.

- **Fichier .h**

   Nom du fichier d’en-tête de classe de consommateur, basé par défaut sur le nom du fichier ou de la source de données de l’ordinateur que vous avez sélectionné.

- **Fichier .cpp**

   Nom du fichier d’implémentation de la classe de consommateur, basé par défaut sur le nom du fichier ou de la source de données de l’ordinateur que vous avez sélectionné.

- **Type**

   Spécifie si le Recordset est une feuille de réponse dynamique (par défaut) ou un instantané.

  - **Dynaset** : spécifie que le jeu d’enregistrements est une feuille de réponse dynamique. Une feuille de réponse dynamique est le résultat d’une requête qui fournit une vue indexée dans les données de la base de données interrogée. Un dynaset met en cache uniquement un index intégral des données d’origine et offre donc un gain de performances sur un instantané. L’index pointe directement vers chaque enregistrement trouvé à la suite d’une requête et indique si un enregistrement est supprimé. Vous avez également accès aux informations mises à jour dans les enregistrements interrogés. Il s’agit de la valeur par défaut.

  - **Snapshot** : spécifie que le jeu d’enregistrements est un instantané. Un instantané est le résultat d’une requête et est une vue d’une base de données à un moment donné. Tous les enregistrements trouvés à la suite de la requête sont mis en cache, de sorte que vous ne voyez pas les modifications apportées aux enregistrements d’origine.

- **Lier toutes les colonnes**

   Spécifie si toutes les colonnes de la table sélectionnée sont liées. Si vous activez cette case à cocher (par défaut), toutes les colonnes sont liées ; Si vous ne cochez pas cette case, aucune colonne n’est liée et vous devez les lier manuellement dans la classe Recordset.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Consommation ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)
