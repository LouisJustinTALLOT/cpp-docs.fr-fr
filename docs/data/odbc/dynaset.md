---
title: Feuille de réponse dynamique | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, dynasets
- ODBC cursor library [ODBC], dynasets
- keyset-driven cursors in dynasets
- cursors [ODBC], keyset-driven cursors in dynasets
- cursor library [ODBC], dynaset availability
- recordsets [C++], dynasets
- dynasets
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ec71b5b00b26564f9c8dc3c2d98f53f8182b0ca3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="dynaset"></a>Feuille de réponse dynamique
Cette rubrique décrit les feuilles de réponse dynamiques et explique leur [disponibilité](#_core_availability_of_dynasets).  
  
> [!NOTE]
>  Cette rubrique s’applique aux classes ODBC MFC, y compris [CRecordset](../../mfc/reference/crecordset-class.md). Pour plus d’informations sur les feuilles de réponse dynamiques dans les classes DAO, consultez [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md). Avec DAO, vous pouvez ouvrir les types d’enregistrements.  
  
 Un jeu de données est un jeu d’enregistrements avec les propriétés dynamiques. Pendant sa durée de vie, un objet recordset en mode de feuille de réponse dynamique (généralement appelé une feuille de réponse dynamique) reste synchronisé avec la source de données de la façon suivante. Dans un environnement multi-utilisateur, les autres utilisateurs peuvent modifier ou supprimer des enregistrements qui se trouvent dans votre feuille de réponse dynamique ou ajouter des enregistrements à la table de que votre feuille de réponse dynamique représente. Enregistrements de votre application ajoute à ou supprime le jeu d’enregistrements sont répercutées dans votre feuille de réponse dynamique. Enregistrements par d’autres utilisateurs à la table seront répercutées dans votre feuille de réponse dynamique jusqu'à ce que vous reconstruisiez la feuille de réponse dynamique en appelant sa **Requery** fonction membre. Lorsque d’autres utilisateurs suppriment des enregistrements, le code MFC ignore les suppressions de votre recordset. Modifications des autres utilisateurs à des enregistrements existants sont reflétées dans votre feuille de réponse dynamique dès que vous accédez à l’enregistrement affecté.  
  
 De même, les modifications apportées aux enregistrements dans une feuille de réponse dynamique sont reflétées dans les feuilles de réponse dynamiques en cours d’utilisation par d’autres utilisateurs. Vous ajoutez des enregistrements ne sont pas répercutées dans les feuilles de réponse dynamiques des autres utilisateurs tant que leur lanciez. Les enregistrements que vous supprimez sont marqués comme « supprimé » dans les recordsets des autres utilisateurs. Si vous avez plusieurs connexions à la même base de données (plusieurs `CDatabase` objets), les jeux d’enregistrements associés à ces connexions ont le même état que les recordsets des autres utilisateurs.  
  
 Feuilles de réponse dynamiques sont plus utiles lorsque les données doivent être dynamiques, (par exemple) dans un système de réservation des compagnies aériennes.  
  
> [!NOTE]
>  Pour utiliser les feuilles de réponse dynamiques, vous devez disposer d’un pilote ODBC pour votre source de données qui prend en charge les feuilles de réponse dynamiques et la bibliothèque de curseurs ODBC ne doit pas être chargée. Pour plus d’informations, consultez [disponibilité des feuilles de réponse dynamiques](#_core_availability_of_dynasets).  
  
 Pour spécifier qu’un recordset est une feuille de réponse dynamique, passez **CRecordset::dynaset** comme premier paramètre à la **ouvrir** fonction membre de l’objet recordset.  
  
> [!NOTE]
>  Modifiables, votre pilote ODBC doit prendre en charge deux instructions de mise à jour positionnée ou **:: SQLSetPos** fonction d’API ODBC. Si les deux sont pris en charge, MFC utilise **:: SQLSetPos** par souci d’efficacité.  
  
##  <a name="_core_availability_of_dynasets"></a> Disponibilité des feuilles de réponse dynamiques  
 Les classes de base de données MFC prennent en charge les feuilles de réponse dynamiques si les conditions suivantes sont remplies :  
  
-   La bibliothèque de curseurs ODBC DLL ne doit pas être en cours d’utilisation pour cette source de données.  
  
     Si la bibliothèque de curseurs est utilisée, elle masque certaines fonctionnalités du pilote ODBC sous-jacent qui est nécessaire pour la prise en charge de la feuille de réponse dynamique. Si vous souhaitez utiliser les feuilles de réponse dynamiques (et si votre pilote ODBC possède les fonctionnalités requises pour les feuilles de réponse dynamiques, comme décrit dans le reste de cette section), vous pouvez provoquer MFC ne pas charger la bibliothèque de curseurs lorsque vous créez un `CDatabase` objet. Pour plus d’informations, consultez [ODBC](../../data/odbc/odbc-basics.md) et [OpenEx](../../mfc/reference/cdatabase-class.md#openex) ou [ouvrir](../../mfc/reference/cdatabase-class.md#open) fonction membre de classe `CDatabase`.  
  
     Dans la terminologie ODBC, feuilles de réponse dynamiques et les instantanés sont appelés curseurs. Un curseur est un mécanisme utilisé pour assurer le suivi de sa position dans un jeu d’enregistrements.  
  
-   Le pilote ODBC de votre source de données doit prendre en charge les curseurs pilotés par jeu de clés.  
  
     Curseurs de gérer les données d’une table en obtenant et le stockage d’un jeu de clés. Les clés sont utilisées pour obtenir les données actuelles de la table lorsque l’utilisateur fait défiler un enregistrement particulier. Pour déterminer si votre pilote fournit cette prise en charge, appelez le **:: SQLGetInfo** fonction d’API ODBC avec le **SQL_SCROLL_OPTIONS** paramètre.  
  
     Si vous essayez d’ouvrir une feuille de réponse dynamique sans prise en charge des jeux de clés, vous obtenez un `CDBException` avec la valeur de code de retour **AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED**.  
  
-   Le pilote ODBC de votre source de données doit prendre en charge l’extraction étendue.  
  
     L’extraction étendue est la possibilité de faire défiler vers l’arrière ainsi que pour transférer les enregistrements résultant de votre requête SQL. Pour déterminer si votre pilote prend en charge cette capacité, appelez le **:: SQLGetFunctions** fonction d’API ODBC avec le **SQL_API_SQLEXTENDEDFETCH** paramètre.  
  
 Si vous souhaitez modifiables (ou des instantanés, dans notre exemple), votre pilote ODBC doit également prendre en charge la **:: SQLSetPos** fonction d’API ODBC ou les mises à jour positionnées. Le **:: SQLSetPos** fonction permet de MFC mettre à jour la source de données sans envoyer d’instructions SQL. Si cette prise en charge est disponible, MFC utilise, plutôt que la mise à jour à l’aide de SQL. Pour déterminer si votre pilote prend en charge **:: SQLSetPos**, appelez **:: SQLGetInfo** avec la **SQL_POS_OPERATIONS** paramètre.  
  
 Mises à jour positionnées utilisent la syntaxe SQL (sous la forme **WHERE CURRENT OF** \<cursorname >) pour identifier une ligne particulière dans la table sur la source de données. Pour déterminer si votre pilote prend en charge les mises à jour positionnées, appelez **:: SQLGetInfo** avec la **SQL_POSITIONED_STATEMENTS** paramètre.  
  
 En règle générale, les feuilles de réponse dynamiques MFC (mais pas avant uniquement des recordsets) nécessitent un pilote ODBC conforme au niveau 2 d’API. Si le pilote de votre source de données est conforme à l’ensemble d’API de niveau 1, vous pouvez toujours utiliser les instantanés modifiables et en lecture seule et recordsets avant uniquement, mais pas les dynasets. Toutefois, un pilote de niveau 1 peut prendre en charge les dynasets si elle prend en charge l’extraction étendue et les curseurs pilotés par jeu de clés. Pour plus d’informations sur les niveaux de conformité ODBC, consultez [ODBC](../../data/odbc/odbc-basics.md).  
  
> [!NOTE]
>  Si vous souhaitez utiliser les instantanés et les feuilles de réponse dynamiques, vous devez les baser sur deux `CDatabase` objets (deux connexions différentes).  
  
 Contrairement aux instantanés qui utilisent un stockage intermédiaire géré par la bibliothèque de curseurs ODBC, feuilles de réponse dynamiques extraire un enregistrement directement à partir de la source de données dès que vous accédez par défilement. Cela permet de conserver les enregistrements sélectionnés à l’origine par la feuille de réponse dynamique synchronisé avec la source de données.  
  
 Pour obtenir la liste des pilotes ODBC inclus dans cette version de Visual C++ et pour plus d’informations sur l’obtention de pilotes supplémentaires, consultez [liste de pilotes ODBC](../../data/odbc/odbc-driver-list.md).  
  
## <a name="see-also"></a>Voir aussi  
 [ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)