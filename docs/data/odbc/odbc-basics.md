---
description: 'En savoir plus sur : notions de base relatives à ODBC'
title: Éléments fondamentaux relatifs à ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC cursor library [ODBC], ODBC components
- ODBC components
- ODBC components, required components
- ODBC, about ODBC
- ODBC, components
ms.assetid: ec529702-0fb2-4754-b8de-d1efa8eca18f
ms.openlocfilehash: 94482abd046645e445ffae7f85f192514f4fff78
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161180"
---
# <a name="odbc-basics"></a>Éléments fondamentaux relatifs à ODBC

Cette rubrique fournit les notions de base de Open Database Connectivity (ODBC) :

- [Fonctionnement d’ODBC avec les classes de base de données](../../data/odbc/odbc-and-the-database-classes.md)

- [Fonctionnement des pilotes ODBC avec les feuilles de réponse dynamiques](../../data/odbc/odbc-driver-requirements-for-dynasets.md)

- [Quels sont les composants ODBC que vous devez redistribuer avec vos applications](../../data/odbc/redistributing-odbc-components-to-your-customers.md)

Vous devez également lire la rubrique connexe [ODBC : bibliothèque de curseurs ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
> Les sources de données ODBC sont accessibles par le biais des classes ODBC MFC, comme décrit dans cette rubrique, ou par le biais des classes d’objets d’accès aux données (DAO) MFC.

> [!NOTE]
> Les classes ODBC MFC prennent en charge Unicode et le multithread. Pour plus d’informations sur la prise en charge du multithreading, consultez [ODBC, classes et threads](../../data/odbc/odbc-classes-and-threads.md) .

ODBC est une interface de niveau d’appel qui permet aux applications d’accéder aux données de n’importe quelle base de données pour laquelle il existe un pilote ODBC. À l’aide d’ODBC, vous pouvez créer des applications de base de données avec un accès à toutes les bases de données pour lesquelles votre utilisateur final dispose d’un pilote ODBC. ODBC fournit une API qui permet à votre application d’être indépendante du système de gestion de bases de données (SGBD) source.

ODBC est la partie base de données de l’architecture WOSA (Microsoft Windows Open Services Architecture), qui est une interface qui permet aux applications de bureau Windows de se connecter à plusieurs environnements informatiques sans réécrire l’application pour chaque plateforme.

Les composants de ODBC sont les suivants :

- API ODBC

   Bibliothèque d’appels de fonction, ensemble de codes d’erreur et syntaxe [SQL](../../data/odbc/sql.md) standard permettant d’accéder aux données sur des SGBD.

- Gestionnaire de pilotes ODBC

   Bibliothèque de liens dynamiques (Odbc32.dll) qui charge les pilotes de base de données ODBC pour le compte d’une application. Cette DLL est transparente pour votre application.

- Pilotes de base de données ODBC

   Une ou plusieurs dll qui traitent les appels de fonction ODBC pour des SGBD spécifiques. Pour obtenir la liste des pilotes fournis, consultez [ODBC Driver List](../../data/odbc/odbc-driver-list.md).

- [Bibliothèque de curseurs ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)

   Bibliothèque de liens dynamiques (Odbccr32.dll) qui réside entre le gestionnaire de pilotes ODBC et les pilotes et gère le défilement des données.

- [Administrateur ODBC](../../data/odbc/odbc-administrator.md)

   Outil utilisé pour configurer un SGBD afin qu’il soit disponible en tant que source de données pour une application.

Une application obtient l’indépendance par rapport aux SGBD en utilisant un pilote ODBC écrit spécifiquement pour un SGBD plutôt que d’utiliser directement le SGBD. Le pilote convertit les appels en commandes que son SGBD peut utiliser, ce qui simplifie le travail du développeur et le rend disponible pour un large éventail de sources de données.

Les classes de base de données prennent en charge toute source de données pour laquelle vous disposez d’un pilote ODBC. Cela peut, par exemple, inclure une base de données relationnelle, une base de données de méthode d’accès séquentiel indexé (ISAM), une feuille de calcul Microsoft Excel ou un fichier texte. Les pilotes ODBC gèrent les connexions à la source de données, et SQL est utilisé pour sélectionner des enregistrements de la base de données.

Pour la liste des pilotes ODBC inclus dans cette version de Visual C++ et pour des informations sur l’obtention de pilotes supplémentaires, consultez la [Liste des pilotes ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="see-also"></a>Voir aussi

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
