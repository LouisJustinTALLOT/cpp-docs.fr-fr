---
title: Prise en charge, Assistant Application MFC de base de données | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.database
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, database support
ms.assetid: 9ddf4558-fd41-4ac7-8d9b-c93d9c68ab59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17b92c58efacc6a4038420eaeae065a7281847be
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723916"
---
# <a name="database-support-mfc-application-wizard"></a>Prise en charge des bases de données, Assistant Application MFC
Cette page fournit des options qui vous permettent de spécifier le niveau de base de données prend en charge (plus une source de données, si nécessaire) pour votre projet.  
  
- **Prise en charge de la base de données**

   Définit le niveau de prise en charge de la base de données pour votre projet.  
  
   |Option|Description|  
   |------------|-----------------|  
   |**Aucun**|Ne fournit aucun support de base de données. Il s'agit de l'option par défaut.|  
   |**Fichiers d’en-tête**|Fournit le niveau de prise en charge de la base de données de base pour votre application. Si vous sélectionnez la prise en charge ODBC sous **type Client**, l’Assistant Application MFC inclut dans votre projet le fichier d’en-tête AFXDB. H. Il ajoute des bibliothèques de liens, mais il ne crée pas de toutes les classes spécifiques à la base de données. Vous pouvez créer ultérieurement des jeux d’enregistrements et les utiliser pour examiner et mettre à jour des enregistrements. Si vous sélectionnez la prise en charge OLE DB sous **type Client**, les fichiers d’en-tête suivants sont inclus : ATLBASE. H AFXOLEDB. FICHIER ATLPLUS H. H|  
   |**Vue de base de données sans prise en charge de fichier**|Inclut les fichiers d’en-tête de base de données, des bibliothèques de liens, une vue d’enregistrement et un jeu d’enregistrements. (Disponible uniquement pour les applications avec le **support de l’architecture Document/vue** option sélectionnée dans le [Type d’Application](../../mfc/reference/application-type-mfc-application-wizard.md) page.) Cette option inclut la prise en charge du document, mais aucune prise en charge de la sérialisation. Si vous choisissez d’inclure une vue de base de données, vous devez spécifier la source de données.|  
   |**Vue de base de données avec prise en charge de fichier**|Inclut les fichiers d’en-tête de base de données, des bibliothèques de liens, une vue d’enregistrement et un jeu d’enregistrements. (Disponible uniquement pour les applications avec le **support de l’architecture Document/vue** option sélectionnée dans le **Type d’Application** page.) Cette option prend en charge la sérialisation de documents, vous pouvez utiliser, par exemple, pour mettre à jour un fichier de profil utilisateur. Applications de base de données opèrent généralement par enregistrement plutôt que sur un fichier par fichier et n’avez pas besoin sérialisation. Toutefois, vous pouvez avoir une utilisation spéciale pour la sérialisation. Si vous choisissez d’inclure une vue de base de données, vous devez spécifier la source de données.|  
  
   > [!NOTE]
   > Sous **prennent en charge de la base de données**, si vous sélectionnez **vue sans prise en charge du fichier de base de données** ou **vue avec prise en charge du fichier de base de données**, diffère de la dérivation de classe de vue, en sur votre **type Client** sélection, comme suit :  
  
   - Si vous sélectionnez **ODBC** sous **type Client**, puis dérive de la classe d’affichage de l’application [CRecordView](../../mfc/reference/crecordview-class.md). Cette classe est associée un [CRecordset](../../mfc/reference/crecordset-class.md)-classe dérivée, ce qui l’Assistant Application MFC crée également pour vous. Cette option vous donne une application basée sur un formulaire dans lequel la vue de l’enregistrement est utilisée pour afficher et mettre à jour des enregistrements dans son jeu d’enregistrements.  
  
   - Si vous sélectionnez **OLE DB** sous **type Client**, puis dérive de la classe d’affichage [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), et il est associé un [CTable](../../data/oledb/ctable-class.md) ou [CCommand](../../data/oledb/ccommand-class.md)-classe dérivée.  
  
- **Type de client**

   Indique si votre projet utilise les classes OLE DB ou ODBC.  
  
   |Option|Description|  
   |------------|-----------------|  
   |**OLE DB**|Lorsque cette option est sélectionnée, cliquez sur le **Source de données** bouton appelle le **propriétés des liaisons de données** Assistant pour vous aider à créer une connexion à une source de données OLE DB.|  
   |**ODBC**|Lorsque cette option est sélectionnée, cliquez sur le **Source de données** bouton appelle le **sélectionner une Source de données** Assistant pour vous aider à créer une connexion à une source de données ODBC.|  
  
- **Source de données**

   Cliquez sur le **Source de données** bouton pour définir une source de données à l’aide du pilote spécifié ou le fournisseur et la base de données. Si vous avez sélectionné OLE DB dans le **type Client** option, ce bouton affiche la **propriétés des liaisons de données** boîte de dialogue. Si vous avez sélectionné ODBC dans le **type Client** option, ce bouton fournit le **sélectionner une Source de données** boîte de dialogue. Cette option est disponible uniquement si vous choisissez d’inclure une vue de base de données dans votre application.  
  
   |Option|Description|  
   |------------|-----------------|  
   |**Propriétés de liaison de données** (OLE DB)|Établit la source de données spécifiée à l’aide du fournisseur OLE DB spécifié. Vous devez spécifier le fournisseur OLE DB, l’emplacement des données, la source de données, les ID d’ouverture de session et (éventuellement) un mot de passe. Pour plus d’informations sur cette boîte de dialogue, consultez **source de données** dans [Assistant Consommateur OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).|  
   |**Sélectionnez la Source de données** (ODBC)|Établit la source de données spécifiée à l’aide du pilote ODBC spécifié. Vous devez sélectionner un nom de source de données pour choisir une table pour la source de données. L’Assistant lie toutes les colonnes de la table aux variables membres d’un `CRecordset`-classe dérivée. Pour plus d’informations sur cette boîte de dialogue, consultez **source de données** dans [Assistant Consommateur ODBC MFC](../../mfc/reference/mfc-odbc-consumer-wizard.md).|  
  
   > [!NOTE]
   > Dans les versions précédentes, en cliquant sur la touche MAJ enfoncée la **Source de données** bouton ouverte une boîte de dialogue Ouvrir le fichier afin que vous puissiez sélectionner un fichier Data Link (.udl). Cette fonctionnalité n’est plus pris en charge.  
  
- **Générer la classe de base de données avec attributs**

   Disponible pour le client OLE DB uniquement. Spécifie si les classes de base de données dans le projet généré utilisent des attributs.  
  
- **Lier toutes les colonnes**

   Disponible pour les clients ODBC uniquement. Spécifie si toutes les colonnes dans la table sélectionnée sont liées. Si vous activez cette case, toutes les colonnes sont liées ; Si vous ne sélectionnez pas cette case, aucune colonne n’est liés, et vous devez les lier manuellement dans la classe de jeu d’enregistrements.  
  
- **Type**

   Disponible pour les clients ODBC uniquement. Spécifie si le recordset est une feuille de réponse dynamique ou un instantané, comme décrit dans le tableau suivant.  
  
   |Option|Description|  
   |------------|-----------------|  
   |**Feuille de réponse dynamique**|Spécifie que le jeu d’enregistrements est une feuille de réponse dynamique. Un jeu de données est le résultat d’une requête qui fournit une vue indexée dans les données de la base de données interrogée. Feuille de réponse dynamique met en cache qu’un index intégral pour les données d’origine et de gagner ainsi offre un performances sur un instantané. L’index pointe directement vers chaque enregistrement trouvé à la suite d’une requête et indique si un enregistrement est supprimé. Vous avez également accès aux informations mises à jour dans les enregistrements interrogées.|  
   |**Instantané**|Spécifie que le jeu d’enregistrements est un instantané. Un instantané est le résultat d’une requête et est une vue dans une base de données à un point dans le temps. Tous les enregistrements trouvés à la suite de la requête sont mis en cache, vous ne voyez pas les modifications apportées aux enregistrements d’origine.|  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)
