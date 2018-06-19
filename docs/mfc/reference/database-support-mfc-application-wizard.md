---
title: Prise en charge, Assistant Application MFC de base de données | Documents Microsoft
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
ms.openlocfilehash: 86c6cd679b69bf84504d6735ca39d572bd48ff07
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372242"
---
# <a name="database-support-mfc-application-wizard"></a>Prise en charge des bases de données, Assistant Application MFC
Cette page fournit des options qui vous permettent de spécifier le niveau de base de données prend en charge (plus une source de données, si nécessaire) pour votre projet.  
  
 **Prise en charge de la base de données**  
 Définit le niveau de prise en charge de la base de données pour votre projet.  
  
|Option|Description|  
|------------|-----------------|  
|**Aucun**|Ne fournit aucune prise en charge de la base de données. Il s'agit de l'option par défaut.|  
|**Fichiers d’en-tête**|Fournit le niveau de prise en charge de la base de données de base pour votre application. Si vous sélectionnez la prise en charge ODBC sous **type Client**, l’Assistant Application MFC inclut dans votre projet, le fichier d’en-tête AFXDB. H. Il ajoute des bibliothèques de liens, mais il ne crée pas de toutes les classes spécifiques à la base de données. Vous pouvez créer des jeux d’enregistrements ultérieurement et les utiliser pour examiner et mettre à jour des enregistrements. Si vous sélectionnez la prise en charge OLE DB sous **type Client**, les fichiers d’en-tête suivants sont inclus : ATLBASE. H AFXOLEDB. FICHIER DE ATLPLUS H. H|  
|**Vue de base de données sans prise en charge de fichier**|Inclut les fichiers d’en-tête de base de données, des bibliothèques de liens, une vue d’enregistrement et un jeu d’enregistrements. (Disponible uniquement pour les applications avec le **prise en charge d’architecture Document/vue** option sélectionnée dans le [Type d’Application](../../mfc/reference/application-type-mfc-application-wizard.md) page.) Cette option inclut la prise en charge du document, mais aucune prise en charge de la sérialisation. Si vous choisissez d’inclure une vue de base de données, vous devez spécifier la source des données.|  
|**Vue de base de données avec prise en charge de fichier**|Inclut les fichiers d’en-tête de base de données, des bibliothèques de liens, une vue d’enregistrement et un jeu d’enregistrements. (Disponible uniquement pour les applications avec le **prise en charge d’architecture Document/vue** option sélectionnée dans le **Type d’Application** page.) Cette option prend en charge la sérialisation de document, vous pouvez utiliser, par exemple, pour mettre à jour d’un fichier de profil utilisateur. Les applications de base de données fonctionnent généralement par enregistrement plutôt que sur un fichier par fichier et n’avez pas besoin sérialisation. Toutefois, vous avez peut-être une utilisation spéciale pour la sérialisation. Si vous choisissez d’inclure une vue de base de données, vous devez spécifier la source des données.|  
  
> [!NOTE]
>  Sous **prennent en charge de la base de données**, si vous sélectionnez **vue sans prise en charge des fichiers de base de données** ou **vue avec prise en charge des fichiers de base de données**, diffère de la dérivation de classe de vue, en sur votre **type Client** sélection, comme suit :  
  
-   Si vous sélectionnez **ODBC** sous **type Client**, puis dérive de la classe de vue de l’application [CRecordView](../../mfc/reference/crecordview-class.md). Cette classe est associée une [CRecordset](../../mfc/reference/crecordset-class.md)-classe dérivée, ce qui l’Assistant Application MFC crée également pour vous. Cette option permet de générer une application basée sur formulaire dans lequel la vue de l’enregistrement est utilisée pour afficher et mettre à jour des enregistrements dans son jeu d’enregistrements.  
  
-   Si vous sélectionnez **OLE DB** sous **type Client**, puis dérive de la classe d’affichage [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), et il est associé à un [CTable](../../data/oledb/ctable-class.md) ou [CCommand](../../data/oledb/ccommand-class.md)-classe dérivée.  
  
 **Type de client**  
 Indique si votre projet utilise des classes OLE DB ou ODBC.  
  
|Option|Description|  
|------------|-----------------|  
|**OLE DB**|Lorsque cette option est sélectionnée, en cliquant sur le **Source de données** bouton appelle la **propriétés des liaisons de données** Assistant pour vous aider à créer une connexion à une source de données OLE DB.|  
|**ODBC**|Lorsque cette option est sélectionnée, en cliquant sur le **Source de données** bouton appelle la **sélectionner une Source de données** Assistant pour vous aider à créer une connexion à une source de données ODBC.|  
  
 **Source de données**  
 Cliquez sur le **Source de données** bouton pour définir une source de données à l’aide du pilote spécifié ou le fournisseur et la base de données. Si vous avez sélectionné OLE DB dans le **type Client** option, ce bouton affiche la **propriétés des liaisons de données** boîte de dialogue. Si vous avez sélectionné ODBC dans le **type Client** option, ce bouton fournit le **sélectionner une Source de données** boîte de dialogue. Cette option est disponible uniquement si vous choisissez d’inclure une vue de base de données dans votre application.  
  
|Option|Description|  
|------------|-----------------|  
|**Propriétés de liaison de données** (OLE DB)|Établit la source de données spécifiée à l’aide du fournisseur OLE DB spécifié. Vous devez spécifier le fournisseur OLE DB, l’emplacement des données, la source de données, les ID d’ouverture de session et (éventuellement) un mot de passe. Pour plus d’informations sur cette boîte de dialogue, consultez **source de données** dans [Assistant Consommateur OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).|  
|**Sélectionnez la Source de données** (ODBC)|Établit la source de données spécifiée à l’aide du pilote ODBC spécifié. Vous devez sélectionner un nom de source de données pour choisir une table pour la source de données. L’Assistant lie toutes les colonnes de la table aux variables membres d’un `CRecordset`-classe dérivée. Pour plus d’informations sur cette boîte de dialogue, consultez **source de données** dans [Assistant Consommateur ODBC MFC](../../mfc/reference/mfc-odbc-consumer-wizard.md).|  
  
> [!NOTE]
>  Dans les versions précédentes, en cliquant sur MAJ le **Source de données** bouton ouverte une boîte de dialogue Ouvrir le fichier pour vous permettre de sélectionner un fichier de liaison de données (.udl). Cette fonctionnalité n’est plus pris en charge.  
  
 **Générer la classe de base de données avec attributs**  
 Disponible pour le client OLE DB uniquement. Spécifie si les classes de base de données dans le projet généré utilisent des attributs.  
  
 **Lier toutes les colonnes**  
 Disponible pour le client ODBC uniquement. Spécifie si toutes les colonnes de la table sélectionnée sont liés. Si vous activez cette case, toutes les colonnes sont liées ; Si vous ne sélectionnez pas cette case, aucune colonne n’est liée et vous devez les lier manuellement dans la classe de recordset.  
  
 **Type**  
 Disponible pour le client ODBC uniquement. Spécifie si le recordset est une feuille de réponse dynamique ou un instantané, comme décrit dans le tableau suivant.  
  
|Option|Description|  
|------------|-----------------|  
|**Feuille de réponse dynamique**|Spécifie que le recordset est une feuille de réponse dynamique. Un jeu de données est le résultat d’une requête qui fournit une vue indexée dans les données de la base de données interrogée. Une feuille de réponse dynamique met en cache qu’un index intégral pour les données d’origine et de gagner ainsi offre de meilleures performances sur un instantané. L’index pointe directement vers chaque enregistrement trouvé à la suite d’une requête et indique si un enregistrement est supprimé. Vous avez également accès aux informations mises à jour dans les enregistrements interrogés.|  
|Instantané|Spécifie que le jeu d’enregistrements est un instantané. Un instantané est le résultat d’une requête et est une vue dans une base de données à un moment donné dans le temps. Tous les enregistrements trouvés à la suite de la requête sont mis en cache, donc vous ne voyez pas les modifications apportées aux enregistrements d’origine.|  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)
