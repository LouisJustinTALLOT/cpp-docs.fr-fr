---
title: Prise en charge des bases de données, Assistant Application MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.database
helpviewer_keywords:
- MFC Application Wizard, database support
ms.assetid: 9ddf4558-fd41-4ac7-8d9b-c93d9c68ab59
ms.openlocfilehash: c13d56d2fee45e130aba81168188bec6d8828d51
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365882"
---
# <a name="database-support-mfc-application-wizard"></a>Prise en charge des bases de données, Assistant Application MFC

Cette page offre des options qui vous permettent de spécifier le niveau de support de base de données (plus une source de données, si nécessaire) pour votre projet.

- **Soutien de base de données**

   Définit le niveau de support de base de données pour votre projet.

   |Option|Description|
   |------------|-----------------|
   |**Aucun**|Fournit aucun support de base de données. Il s'agit de l'option par défaut.|
   |**Fichiers d’en-tête seulement**|Fournit le niveau de base de la prise en charge de base pour votre application. Si vous sélectionnez le support ODBC sous **type client,** l’assistant d’application MFC inclut dans votre projet le fichier d’en-tête AFXDB. H. Il ajoute des bibliothèques de liens, mais il ne crée pas de classes spécifiques à la base de données. Vous pouvez créer des enregistrements plus tard et les utiliser pour examiner et mettre à jour les enregistrements. Si vous sélectionnez le support OLE DB sous **type Client,** les fichiers d’en-tête suivants sont inclus : ATLBASE. H AFXOLEDB. H ATLPLUS. H (en)|
   |**Vue de base de données sans prise en charge de fichiers**|Inclut les fichiers d’en-tête de base de données, les bibliothèques de liaison, une vue d’enregistrement et un ensemble d’enregistrements. (Disponible uniquement pour les applications avec l’option **de support d’architecture Document/vue** sélectionnée dans la page [Type d’application.)](../../mfc/reference/application-type-mfc-application-wizard.md) Cette option comprend l’assistance documentaire, mais pas de support de sérialisation. Si vous choisissez d’inclure une vue de base de données, vous devez spécifier la source des données.|
   |**Vue de base de données avec prise en charge de fichiers**|Inclut les fichiers d’en-tête de base de données, les bibliothèques de liaison, une vue d’enregistrement et un ensemble d’enregistrements. (Disponible uniquement pour les applications avec l’option **de support d’architecture Document/vue** sélectionnée dans la page **Type d’application.)** Cette option prend en charge la sérialisation des documents, que vous pouvez utiliser, par exemple, pour mettre à jour un fichier de profil utilisateur. Les applications de base de données fonctionnent généralement selon les dossiers plutôt que sur une base par fichier et n’ont donc pas besoin de sérialisation. Cependant, vous pouvez avoir une utilisation spéciale pour la sérialisation. Si vous choisissez d’inclure une vue de base de données, vous devez spécifier la source des données.|

   > [!NOTE]
   > Dans le cadre **de la base de données Support**, si vous sélectionnez soit la vue de base de données sans prise de charge de **fichiers** ou la vue de base de données avec la prise en charge de **fichier,** la dérivation de classe de vue diffère, selon votre sélection **de type Client,** comme suit :

  - Si vous sélectionnez **ODBC** sous **type Client,** alors la classe de vue de l’application provient de [CRecordView](../../mfc/reference/crecordview-class.md). Cette classe est associée à une classe dérivée de [CRecordset,](../../mfc/reference/crecordset-class.md)que le MFC Application Wizard crée également pour vous. Cette option vous donne une application basée sur un formulaire dans laquelle la vue d’enregistrement est utilisée pour afficher et mettre à jour les enregistrements à travers son ensemble d’enregistrements.

  - Si vous sélectionnez **OLE DB** sous **type Client,** alors la classe de vue dérive de [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), et il est associé à une classe [CTable](../../data/oledb/ctable-class.md) ou [CCommand-dérivé.](../../data/oledb/ccommand-class.md)

- **Type de client**

   Indique si votre projet utilise des cours OLE DB ou ODBC.

   |Option|Description|
   |------------|-----------------|
   |**OLE DB**|Lorsque cette option est sélectionnée, en cliquant sur le bouton **Source de données** invoque **l’assistant Data Link Properties** pour vous aider à créer une connexion à une source de données OLE DB.|
   |**ODBC**|Lorsque cette option est sélectionnée, en cliquant sur le bouton **Source de données** invoque **l’assistant Select Data Source** pour vous aider à créer une connexion à une source de données ODBC.|

- **Source de données**

   > [!NOTE]
   > L’ASSISTANT consommateur ATL OLE DB et MFC ODBC Consumer Wizard ne sont pas disponibles dans Visual Studio 2019 et plus tard. Vous pouvez toujours ajouter la fonctionnalité manuellement. Pour plus d’informations, consultez [Création d’un consommateur sans utiliser l’Assistant](../../data/oledb/creating-a-consumer-without-using-a-wizard.md).

   Cliquez sur le bouton **Source de données** pour configurer une source de données à l’aide du pilote ou du fournisseur et de la base de données spécifiés. Si vous avez sélectionné OLE DB dans l’option **de type Client,** ce bouton affiche la boîte de dialogue **Data Link Properties.** Si vous avez sélectionné ODBC dans l’option **de type Client,** ce bouton fournit la boîte de dialogue **Select Data Source.** Cette option n’est disponible que si vous choisissez d’inclure une vue de base de données dans votre application.

   |Option|Description|
   |------------|-----------------|
   |**Propriétés de liaison de données** (OLE DB)|Établit la source de données spécifiée à l’aide du fournisseur OLE DB spécifié. Vous devez spécifier le fournisseur OLE DB, l’emplacement des données, la source de données, l’ID logon et (optionnellement) un mot de passe. Pour plus de détails sur cette boîte de dialogue, voir **Source de données** dans [ATL OLE DB Consumer Wizard](../../atl/reference/atl-ole-db-consumer-wizard.md).|
   |**Sélectionnez Source de données** (ODBC)|Établit la source de données spécifiée à l’aide du conducteur ODBC spécifié. Vous devez sélectionner un nom source de données pour choisir une table pour la source de données. L’assistant lie toutes les colonnes de `CRecordset`la table aux variables membres d’une classe dérivée. Pour plus de détails sur cette boîte de dialogue, voir **Source de données** dans [MFC ODBC Consumer Wizard](../../mfc/reference/mfc-odbc-consumer-wizard.md).|

- **Générer la classe de base de données attribuée**

   Disponible uniquement pour le client OLE DB. Précise si les classes de base de données dans les attributs générés par le projet utilisent.

- **Lier toutes les colonnes**

   Disponible uniquement pour le client ODBC. Précise si toutes les colonnes du tableau sélectionné sont liées. Si vous sélectionnez cette boîte, toutes les colonnes sont liées; si vous ne sélectionnez pas cette boîte, aucune colonne n’est liée, et vous devez les lier manuellement dans la classe de recordet.

- **Type**

   Disponible uniquement pour le client ODBC. Précise si le jeu d’enregistrement est un dynaset ou un instantané, tel que décrit dans le tableau suivant.

   |Option|Description|
   |------------|-----------------|
   |**Feuille de réponse dynamique**|Précise que le recordet est un dynaset. Un dynaset est le résultat d’une requête qui fournit une vue indexée dans les données de la base de données demandée. Un dynaset cache seulement un index intégral aux données originales et offre ainsi un gain de performance sur un instantané. L’index indique directement chaque enregistrement trouvé à la suite d’une requête et indique si un enregistrement est supprimé. Vous avez également accès à des informations mises à jour dans les dossiers interrogés.|
   |**Instantané**|Spécifie que le livre est un instantané. Un instantané est le résultat d’une requête et est une vue dans une base de données à un moment donné dans le temps. Tous les enregistrements trouvés à la suite de la requête sont mis en cache, de sorte que vous ne voyez pas de modifications aux enregistrements originaux.|

## <a name="see-also"></a>Voir aussi

[Assistant d’application MFC](../../mfc/reference/mfc-application-wizard.md)
