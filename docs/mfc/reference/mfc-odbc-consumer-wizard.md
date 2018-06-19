---
title: Assistant Consommateur ODBC MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.class.mfc.consumer.overview
dev_langs:
- C++
helpviewer_keywords:
- MFC ODBC Consumer Wizard
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c8a707df6878cd0031cb2ec9b06285e568503992
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371422"
---
# <a name="mfc-odbc-consumer-wizard"></a>Consommateur ODBC MFC (Assistant)
Insérez « Résultats de recherche « résumé ici.  
  
 Cet Assistant définit une classe de recordset ODBC et les liaisons de données nécessaire pour accéder à la source de données spécifié.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Source de données**  
 Le **Source de données** bouton vous permet de définir la source de données spécifiée à l’aide du pilote ODBC spécifié. Pour plus d’informations sur les fichiers de source de données (DSN), consultez [des Sources de données fichier](https://msdn.microsoft.com/library/ms715401.aspx) dans le SDK ODBC. Le **sélectionner une Source de données** boîte de dialogue comporte deux onglets :  
  
-   **Source de données fichier** onglet : le **Regarder dans** zone spécifie le répertoire dans lequel sélectionner les fichiers à utiliser comme sources de données. La valeur par défaut est \Program Files\ODBC\Data Sources. Les sources de données de fichiers existants (fichiers .dsn) s’affichent dans la zone de liste principale. Vous pouvez configurer les sources de données avant l’heure à l’aide de la **DSN de fichier** onglet sur le [administrateur de sources de données ODBC](https://msdn.microsoft.com/library/ms714024.aspx), ou créer de nouveaux à l’aide de cette boîte de dialogue.  
  
     Pour créer une nouvelle source de données de fichiers à partir de cette boîte de dialogue, cliquez sur `New` pour spécifier un nom de source de données ; la **créer une nouvelle Source de données** boîte de dialogue s’affiche. Dans le **créer une nouvelle Source de données** boîte de dialogue, sélectionnez un pilote approprié puis cliquez sur `Next`; cliquez sur **Parcourir**, puis sélectionnez le nom du fichier à utiliser comme source de données (vous devez sélectionner « Tous les fichiers » pour afficher les fichiers non DSN, tels que des fichiers .xls) ; Cliquez sur `Next`, puis cliquez sur **Terminer**. (Si vous avez sélectionné un fichier non DSN, vous obtiendrez une boîte de dialogue de spécifiques au pilote, tels que « Installation ODBC pour Microsoft Excel, » qui convertira le fichier à une source de données.)  
  
    > [!NOTE]
    >  Vous pouvez également créer une nouvelle source de données de fichiers au préalable à l’aide de l’administrateur de Source de données ODBC. À partir de la **Démarrer** menu, sélectionnez **paramètres**, **le panneau de configuration**, **outils d’administration**, **deSourcesdedonnées(ODBC)**, puis **administrateur de sources de données ODBC**.  
  
     Le **nom DSN** boîte permet de vous permet de spécifier un nom pour la source de données de fichier. Vous devez vous assurer que le nom de la source de données se termine avec l’extension de fichier approprié, tel que .xls pour les fichiers Excel ou .mdb pour accéder aux fichiers.  
  
     Pour plus d’informations sur les sources de données, consultez [des Sources de données fichier](https://msdn.microsoft.com/library/ms715401.aspx) dans le SDK ODBC.  
  
-   **Source de données de l’ordinateur** onglet : cet onglet répertorie les sources système et données utilisateur. Sources de données utilisateur sont spécifiques à un utilisateur sur cet ordinateur. Sources de données système peuvent être utilisés par tous les utilisateurs sur cet ordinateur ou d’un service système. Consultez [des Sources de données de l’ordinateur](https://msdn.microsoft.com/library/ms710952.aspx) dans le Kit de développement ODBC  
  
 Pour plus d’informations sur les sources de données ODBC, consultez [des Sources de données](https://msdn.microsoft.com/library/ms711688.aspx) dans le SDK ODBC.  
  
 Cliquez sur **OK** se termine. Le **sélectionner un objet de base de données** boîte de dialogue s’affiche. Cette boîte de dialogue, sélectionnez la table ou afficher que le consommateur doit utiliser. Notez que vous pouvez sélectionner plusieurs vues et tables en maintenant la touche CTRL tout en cliquant sur les éléments.  
  
 **Classe**  
 Le nom de la classe de consommateur, en fonction du nom de la source de données de fichier ou l’ordinateur que vous avez sélectionné par défaut.  
  
 **fichier .h**  
 Le nom du consommateur en-tête du fichier de classe, en fonction du nom de la source de données de fichier ou l’ordinateur que vous avez sélectionné par défaut.  
  
 **fichier .cpp**  
 Le nom du consommateur implémentation d’un fichier de classe, en fonction du nom de la source de données de fichier ou l’ordinateur que vous avez sélectionné par défaut.  
  
 **Type**  
 Spécifie si le jeu d’enregistrements est une feuille de réponse dynamique (par défaut) ou un instantané.  
  
-   **Feuille de réponse dynamique**: Spécifie que le recordset est une feuille de réponse dynamique. Un jeu de données est le résultat d’une requête qui fournit une vue indexée dans les données de la base de données interrogée. Une feuille de réponse dynamique met en cache qu’un index intégral pour les données d’origine et de gagner ainsi offre de meilleures performances sur un instantané. L’index pointe directement vers chaque enregistrement trouvé à la suite d’une requête et indique si un enregistrement est supprimé. Vous avez également accès aux informations mises à jour dans les enregistrements interrogés. Il s'agit de la valeur par défaut.  
  
-   **Instantané**: Spécifie que le jeu d’enregistrements est un instantané. Un instantané est le résultat d’une requête et est une vue dans une base de données à un moment donné dans le temps. Tous les enregistrements trouvés à la suite de la requête sont mis en cache, donc vous ne voyez pas les modifications apportées aux enregistrements d’origine.  
  
 **Lier toutes les colonnes**  
 Spécifie si toutes les colonnes de la table sélectionnée sont liés. Si vous activez cette case (par défaut), toutes les colonnes sont liées ; Si vous ne sélectionnez pas cette case, aucune colonne n’est liée et vous devez les lier manuellement dans la classe de recordset.  
  
## <a name="see-also"></a>Voir aussi  
 [MFC ODBC, consommation](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)

