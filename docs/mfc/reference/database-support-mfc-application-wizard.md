---
description: 'En savoir plus sur : prise en charge des bases de données, Assistant Application MFC'
title: Prise en charge des bases de données, Assistant Application MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.database
helpviewer_keywords:
- MFC Application Wizard, database support
ms.assetid: 9ddf4558-fd41-4ac7-8d9b-c93d9c68ab59
ms.openlocfilehash: 4c6f980155e980c772b5ee78f83c80a236998b91
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220303"
---
# <a name="database-support-mfc-application-wizard"></a>Prise en charge des bases de données, Assistant Application MFC

Cette page fournit des options qui vous permettent de spécifier le niveau de prise en charge de base de données (plus une source de données, si nécessaire) pour votre projet.

- **Prise en charge des bases de données**

   Définit le niveau de prise en charge de base de données pour votre projet.

   |Option|Description|
   |------------|-----------------|
   |**Aucun**|Ne fournit aucune prise en charge de base de données. Il s'agit de l'option par défaut.|
   |**Fichiers d’en-tête uniquement**|Fournit le niveau de base de la prise en charge de base de données pour votre application. Si vous sélectionnez prise en charge ODBC sous **type de client**, l’Assistant Application MFC comprend dans votre projet le fichier d’en-tête AFXDB. H. Elle ajoute des bibliothèques de liens, mais elle ne crée pas de classes spécifiques à la base de données. Vous pouvez créer des jeux d’enregistrements ultérieurement et les utiliser pour examiner et mettre à jour des enregistrements. Si vous sélectionnez OLE DB prise en charge sous **type de client**, les fichiers d’en-tête suivants sont inclus : atlbase. H AFXOLEDB. H ATLPLUS. Manutention|
   |**Vue de base de données sans prise en charge des fichiers**|Comprend les fichiers d’en-tête de base de données, les bibliothèques de liens, une vue d’enregistrement et un Recordset. (Disponible uniquement pour les applications avec l’option de **prise en charge de l’architecture document/vue** sélectionnée dans la page [type d’application](../../mfc/reference/application-type-mfc-application-wizard.md) .) Cette option comprend la prise en charge des documents, mais sans prise en charge de la sérialisation. Si vous choisissez d’inclure une vue de base de données, vous devez spécifier la source des données.|
   |**Vue de base de données avec prise en charge des fichiers**|Comprend les fichiers d’en-tête de base de données, les bibliothèques de liens, une vue d’enregistrement et un Recordset. (Disponible uniquement pour les applications avec l’option de **prise en charge de l’architecture document/vue** sélectionnée dans la page **type d’application** .) Cette option prend en charge la sérialisation de documents, que vous pouvez utiliser, par exemple, pour mettre à jour un fichier de profil utilisateur. En règle générale, les applications de base de données opèrent sur la base d’un enregistrement plutôt que sur une base par fichier et n’ont donc pas besoin d’être sérialisées. Toutefois, vous pouvez avoir une utilisation spéciale pour la sérialisation. Si vous choisissez d’inclure une vue de base de données, vous devez spécifier la source des données.|

   > [!NOTE]
   > Sous **prise en charge des bases de** données, si vous sélectionnez l’option **vue de base de données sans prise en** charge des fichiers ou **vue de base de données avec prise en charge des fichiers**, la dérivation de classe d’affichage diffère selon la sélection de votre **type de client** , comme suit :

  - Si vous sélectionnez **ODBC** sous **type de client**, la classe d’affichage de l’application dérive de [CRecordView](../../mfc/reference/crecordview-class.md). Cette classe est associée à une classe dérivée de [CRecordset](../../mfc/reference/crecordset-class.md), que l’Assistant Application MFC crée également pour vous. Cette option vous donne une application basée sur les formulaires dans laquelle la vue d’enregistrement est utilisée pour afficher et mettre à jour des enregistrements via son Recordset.

  - Si vous sélectionnez **OLE DB** sous **type de client**, la classe de vue dérive de [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)et est associée à une classe dérivée de [CTable](../../data/oledb/ctable-class.md) ou de [CCommand](../../data/oledb/ccommand-class.md).

- **Type de client**

   Indique si votre projet utilise des classes OLE DB ou ODBC.

   |Option|Description|
   |------------|-----------------|
   |**OLE DB**|Lorsque cette option est sélectionnée, le fait de cliquer sur le bouton **source de données** appelle l’Assistant propriétés des **liaisons de données** pour vous aider à créer une connexion à une source de données OLE DB.|
   |**ODBC**|Lorsque cette option est sélectionnée, le fait de cliquer sur le bouton **source de données** appelle l’Assistant sélectionner une **source de données** pour vous aider à créer une connexion à une source de données ODBC.|

- **Source de données**

   > [!NOTE]
   > L’Assistant consommateur d’OLE DB ATL et l’Assistant consommateur ODBC MFC ne sont pas disponibles dans Visual Studio 2019 et versions ultérieures. Vous pouvez toujours ajouter la fonctionnalité manuellement. Pour plus d’informations, consultez [Création d’un consommateur sans utiliser l’Assistant](../../data/oledb/creating-a-consumer-without-using-a-wizard.md).

   Cliquez sur le bouton **source de données** pour configurer une source de données à l’aide du pilote ou du fournisseur et de la base de données spécifiés. Si vous avez sélectionné OLE DB dans l’option **type de client** , ce bouton affiche la boîte de dialogue Propriétés des **liaisons de données** . Si vous avez sélectionné ODBC dans l’option **type de client** , ce bouton affiche la boîte de dialogue Sélectionner une **source de données** . Cette option est disponible uniquement si vous choisissez d’inclure une vue de base de données dans votre application.

   |Option|Description|
   |------------|-----------------|
   |**Propriétés des liaisons de données** (OLE DB)|Établit la source de données spécifiée à l’aide du fournisseur de OLE DB spécifié. Vous devez spécifier le fournisseur de OLE DB, l’emplacement des données, la source de données, l’ID de connexion et (éventuellement) un mot de passe. Pour plus d’informations sur cette boîte de dialogue, consultez **source de données** dans [ATL OLE DB Assistant consommateur](../../atl/reference/atl-ole-db-consumer-wizard.md).|
   |**Sélectionner une source de données** (ODBC)|Établit la source de données spécifiée à l’aide du pilote ODBC spécifié. Vous devez sélectionner un nom de source de données pour choisir une table pour la source de données. L’Assistant lie toutes les colonnes de la table aux variables membres d’une `CRecordset` classe dérivée de. Pour plus d’informations sur cette boîte de dialogue, consultez **source de données** dans l' [Assistant consommateur ODBC MFC](../../mfc/reference/mfc-odbc-consumer-wizard.md).|

- **Générer la classe de base de données avec attributs**

   Disponible pour OLE DB client uniquement. Spécifie si les classes de base de données dans le projet généré utilisent des attributs.

- **Lier toutes les colonnes**

   Disponible pour le client ODBC uniquement. Spécifie si toutes les colonnes de la table sélectionnée sont liées. Si vous activez cette case à cocher, toutes les colonnes sont liées ; Si vous ne cochez pas cette case, aucune colonne n’est liée et vous devez les lier manuellement dans la classe Recordset.

- **Type**

   Disponible pour le client ODBC uniquement. Spécifie si le Recordset est une feuille de réponse dynamique ou un instantané, comme décrit dans le tableau suivant.

   |Option|Description|
   |------------|-----------------|
   |**Feuille de réponse dynamique**|Spécifie que le jeu d’enregistrements est une feuille de réponse dynamique. Une feuille de réponse dynamique est le résultat d’une requête qui fournit une vue indexée dans les données de la base de données interrogée. Un dynaset met en cache uniquement un index intégral des données d’origine et offre donc un gain de performances sur un instantané. L’index pointe directement vers chaque enregistrement trouvé à la suite d’une requête et indique si un enregistrement est supprimé. Vous avez également accès aux informations mises à jour dans les enregistrements interrogés.|
   |**Instantané**|Spécifie que le jeu d’enregistrements est un instantané. Un instantané est le résultat d’une requête et est une vue d’une base de données à un moment donné. Tous les enregistrements trouvés à la suite de la requête sont mis en cache, de sorte que vous ne voyez pas les modifications apportées aux enregistrements d’origine.|

## <a name="see-also"></a>Voir aussi

[Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)
