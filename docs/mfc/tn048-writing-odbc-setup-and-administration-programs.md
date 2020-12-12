---
description: 'En savoir plus sur : TN048 : écriture de programmes d’installation et d’administration ODBC pour les applications de base de données MFC'
title: "TN048 : écriture de programmes d'installation et d'administration ODBC pour les applications de base de données MFC"
ms.date: 11/04/2016
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
ms.openlocfilehash: bca8616bae8f7243b9e66b2eccc980afa3865842
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215103"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048 : écriture de programmes d'installation et d'administration ODBC pour les applications de base de données MFC

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Les applications qui utilisent des classes de base de données MFC auront besoin d’un programme d’installation qui installe les composants ODBC. Ils peuvent également avoir besoin d’un programme d’administration ODBC qui récupère des informations sur les pilotes disponibles, pour spécifier des pilotes par défaut et pour configurer des sources de données. Cette note décrit l’utilisation de l’API du programme d’installation ODBC pour écrire ces programmes.

## <a name="writing-an-odbc-setup-program"></a><a name="_mfcnotes_writing_an_odbc_setup_program"></a> Écriture d’un programme d’installation ODBC

Une application de base de données MFC exige que le gestionnaire de pilotes ODBC (ODBC.DLL) et les pilotes ODBC puissent accéder aux sources de données. De nombreux pilotes ODBC nécessitent également des dll réseau et de communication supplémentaires. La plupart des pilotes ODBC sont fournis avec un programme d’installation qui installe les composants ODBC requis. Les développeurs d’applications qui utilisent les classes de base de données MFC peuvent :

- Utilisez les programmes d’installation spécifiques au pilote pour installer les composants ODBC. Cela ne nécessitera aucune autre tâche de la part du développeur : vous pouvez simplement redistribuer le programme d’installation du pilote.

- Vous pouvez également écrire votre propre programme d’installation, qui installe le gestionnaire de pilotes et le pilote.

L’API du programme d’installation ODBC peut être utilisée pour écrire des programmes d’installation spécifiques à l’application. Les fonctions de l’API du programme d’installation sont implémentées par la DLL du programme d’installation ODBC, ODBCINST.DLL sur Windows 16 bits et ODBCCP32.DLL sur Win32. Une application peut appeler `SQLInstallODBC` la dll du programme d’installation, qui installe le gestionnaire de pilotes ODBC, les pilotes ODBC et tous les convertisseurs requis. Il enregistre ensuite les pilotes et les convertisseurs installés dans le fichier ODBCINST.INI (ou le registre, sous NT). `SQLInstallODBC` nécessite le chemin d’accès complet à ODBC. Fichier INF, qui contient la liste des pilotes à installer et décrit les fichiers qui composent chaque pilote. Il contient également des informations similaires sur le gestionnaire de pilotes et les traducteurs. ODBC. Les fichiers INF sont généralement fournis par les développeurs de pilotes.

Un programme peut également installer des composants ODBC individuels. Pour installer le gestionnaire de pilotes, un programme appelle d’abord `SQLInstallDriverManager` dans la dll du programme d’installation pour obtenir le répertoire cible du gestionnaire de pilotes. Il s’agit généralement du répertoire dans lequel résident les dll Windows. Le programme utilise ensuite les informations de la section [ODBC Driver Manager] du pilote ODBC. Fichier INF pour copier le gestionnaire de pilotes et les fichiers associés à partir du disque d’installation dans ce répertoire. Pour installer un pilote individuel, un programme appelle d’abord `SQLInstallDriver` dans la dll du programme d’installation pour ajouter la spécification du pilote au fichier ODBCINST.INI (ou au registre, sous NT). `SQLInstallDriver` retourne le répertoire cible du pilote (généralement le répertoire dans lequel résident les dll Windows). Le programme utilise ensuite les informations de la section du pilote ODBC. Fichier INF pour copier la DLL du pilote et les fichiers associés à partir du disque d’installation dans ce répertoire.

Pour plus d’informations sur ODBC. INF, ODBCINST.INI et l’utilisation de l’API du programme d’installation, consultez *Guide de référence du programmeur* ODBC SDK, chapitre 19, installation de logiciels ODBC.

## <a name="writing-an-odbc-administrator"></a><a name="_mfcnotes_writing_an_odbc_administrator"></a> Écriture d’un administrateur ODBC

Une application de base de données MFC peut configurer et configurer des sources de données ODBC de l’une des deux manières suivantes :

- Utilisez l’administrateur ODBC (disponible en tant que programme ou élément du panneau de configuration).

- Créez votre propre programme pour configurer des sources de données.

Un programme qui configure des sources de données effectue des appels de fonction vers la DLL du programme d’installation. La DLL du programme d’installation appelle une DLL d’installation pour configurer une source de données. Il existe une DLL d’installation pour chaque pilote ; Il peut s’agir de la DLL du pilote, ou d’une DLL distincte. La DLL d’installation invite l’utilisateur à entrer les informations dont le pilote a besoin pour se connecter à la source de données et au traducteur par défaut, s’il est pris en charge. Il appelle ensuite la DLL du programme d’installation et les API Windows pour enregistrer ces informations dans le fichier de ODBC.INI (ou le registre).

Pour afficher une boîte de dialogue avec laquelle un utilisateur peut ajouter, modifier et supprimer des sources de données, un programme appelle `SQLManageDataSources` dans la dll du programme d’installation. Cette fonction est appelée lorsque la DLL du programme d’installation est appelée à partir du panneau de configuration. Pour ajouter, modifier ou supprimer une source de données, `SQLManageDataSources` appelle `ConfigDSN` la dll d’installation pour le pilote associé à cette source de données. Pour ajouter, modifier ou supprimer directement des sources de données, un programme appelle `SQLConfigDataSource` dans la dll du programme d’installation. Le programme passe le nom de la source de données et une option qui spécifie l’action à entreprendre. `SQLConfigDataSource` appelle `ConfigDSN` dans la dll d’installation et lui transmet les arguments de `SQLConfigDataSource` .

Pour plus d’informations, consultez *Guide de référence du programmeur du kit de* développement logiciel (SDK) ODBC, chapitre 23, référence des fonctions dll du programme d’installation et chapitre 24, référence des fonctions dll du programme d’installation

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
