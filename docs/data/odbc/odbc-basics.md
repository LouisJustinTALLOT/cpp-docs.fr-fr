---
title: Principes de base ODBC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC cursor library [ODBC], ODBC components
- ODBC components
- ODBC components, required components
- ODBC, about ODBC
- ODBC, components
ms.assetid: ec529702-0fb2-4754-b8de-d1efa8eca18f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 69b3694292171f00e03cdb941def27fd9e8ffc84
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090297"
---
# <a name="odbc-basics"></a>Éléments fondamentaux relatifs à ODBC
Cette rubrique fournit les principes de base de base de données ODBC (Open Connectivity) :  
  
-   [Fonctionne d’ODBC avec les Classes de base de données](../../data/odbc/odbc-and-the-database-classes.md)  
  
-   [Fonctionnement des pilotes ODBC avec des feuilles de réponse dynamiques](../../data/odbc/odbc-driver-requirements-for-dynasets.md)  
  
-   [Quels composants ODBC que vous devez redistribuer avec vos Applications](../../data/odbc/redistributing-odbc-components-to-your-customers.md)  
  
 Vous devez également consulter la rubrique [ODBC : bibliothèque de curseurs ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
> [!NOTE]
>  Sources de données ODBC sont accessibles via les classes ODBC MFC, comme décrit dans cette rubrique, ou via les classes MFC DAO Data Access Object ().  
  
> [!NOTE]
>  Les classes ODBC MFC prennent en charge Unicode et le multithreading. Pour plus d’informations sur la prise en charge le multithreading, consultez [Threads et Classes ODBC](../../data/odbc/odbc-classes-and-threads.md)  
  
 ODBC est une interface de niveau d’appel qui permet aux applications d’accéder aux données dans une base de données pour lesquelles il existe un pilote ODBC. À l’aide d’ODBC, vous pouvez créer des applications de base de données avec un accès aux bases de données pour laquelle l’utilisateur final possède un pilote ODBC. ODBC fournit une API qui permet à votre application d’être indépendante du système de gestion de base de données (SGBD) source.  
  
 ODBC est la partie de la base de données de la Microsoft Services Architecture WOSA (Windows Open), qui est une interface qui permet aux applications de bureau Windows de se connecter à plusieurs environnements informatiques sans réécriture de l’application pour chaque plateforme.  
  
 Composants de ODBC sont les suivants :  
  
-   API ODBC  
  
     Une bibliothèque de la fonction appelle, un ensemble de codes d’erreur et une norme [SQL](../../data/odbc/sql.md) syntaxe pour accéder aux données SGBD.  
  
-   Gestionnaire de pilotes ODBC  
  
     Une bibliothèque de liens dynamiques (Odbc32.dll) qui charge les pilotes de base de données ODBC pour le compte d’une application. Cette DLL est transparente pour votre application.  
  
-   Pilotes de base de données ODBC  
  
     Une ou plusieurs DLL qui traitent les appels de fonction ODBC pour des SGBD spécifiques. Pour obtenir la liste des pilotes fournis, consultez [liste de pilotes ODBC](../../data/odbc/odbc-driver-list.md).  
  
-   [Bibliothèque de curseurs ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
     Une bibliothèque de liens dynamiques (Odbccr32.dll) qui réside entre le Gestionnaire de pilotes ODBC et les pilotes et gère le défilement des données.  
  
-   [Administrateur ODBC](../../data/odbc/odbc-administrator.md)  
  
     Un outil utilisé pour la configuration d’un système SGBD pour le rendre disponible en tant que source de données pour une application.  
  
 Une application permet d’obtenir l’indépendance de SGBD par travail via un pilote ODBC spécifiquement écrit pour un SGBD, au lieu de travailler directement avec le SGBD. Le pilote traduit les appels en commandes que son SGBD permettre utiliser, ce qui simplifie le travail du développeur et la rendre disponible pour un large éventail de sources de données.  
  
 Les classes de base de données prend en charge n’importe quelle source de données pour lequel vous avez un pilote ODBC. Cela vous permet, par exemple, inclure une base de données relationnelle, une base de données Access méthode ISAM (Indexed Sequential), une feuille de calcul Microsoft Excel ou un fichier texte. Les pilotes ODBC gèrent les connexions à la source de données et SQL est utilisé pour sélectionner des enregistrements de la base de données.  
  
 Pour obtenir la liste des pilotes ODBC inclus dans cette version de Visual C++ et pour plus d’informations sur l’obtention de pilotes supplémentaires, consultez [liste de pilotes ODBC](../../data/odbc/odbc-driver-list.md).  
  
## <a name="see-also"></a>Voir aussi  
 [ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)