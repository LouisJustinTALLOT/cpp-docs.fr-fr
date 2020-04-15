---
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
ms.openlocfilehash: d25520c4ffc805701dfe6b51192f8078e2fa300f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365480"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048 : écriture de programmes d'installation et d'administration ODBC pour les applications de base de données MFC

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Les applications utilisant les classes de base de données MFC auront besoin d’un programme d’installation qui installe des composants ODBC. Ils peuvent également avoir besoin d’un programme d’administration ODBC qui récupérera des informations sur les pilotes disponibles, pour spécifier les conducteurs par défaut et pour configurer les sources de données. Cette note décrit l’utilisation de l’API Installateur ODBC pour écrire ces programmes.

## <a name="writing-an-odbc-setup-program"></a><a name="_mfcnotes_writing_an_odbc_setup_program"></a>Rédaction d’un programme d’installation ODBC

Une application de base de données MFC nécessite le gestionnaire de pilote ODBC (ODBC. DLL) et les conducteurs DDBC pour être en mesure d’obtenir des sources de données. De nombreux conducteurs d’ODBC ont également besoin de DLL réseau et de communication supplémentaires. La plupart des pilotes ODBC expédient avec un programme d’installation qui installera les composants ODBC requis. Les développeurs d’applications utilisant les classes de base de données MFC peuvent :

- S’appuyer sur les programmes d’installation spécifiques au conducteur pour l’installation de composants ODBC. Cela ne nécessitera aucun autre travail de la part du développeur - vous pouvez simplement redistribuer le programme d’installation du pilote.

- Alternativement, vous pouvez écrire votre propre programme d’installation, qui installera le gestionnaire de pilote et le conducteur.

L’installateur ODBC API peut être utilisé pour écrire des programmes d’installation spécifiques à l’application. Les fonctions dans l’installateur API sont mises en œuvre par l’installateur DLL ODBC - ODBCINST. DLL sur 16 bits Windows et ODBCCP32. DLL sur Win32. Une application `SQLInstallODBC` peut faire appel à l’installateur DLL, qui installera le gestionnaire de pilote ODBC, les pilotes ODBC, et tous les traducteurs requis. Il enregistre ensuite les pilotes et les traducteurs installés dans l’ODBCINST. Fichier INI (ou le registre, sur NT). `SQLInstallODBC`exige le chemin complet vers l’ODBC. Fichier INF, qui contient la liste des pilotes à installer et décrit les fichiers qui composent chaque pilote. Il contient également des informations similaires sur le gestionnaire de chauffeur et les traducteurs. Odbc. Les fichiers INF sont généralement fournis par les développeurs de pilotes.

Un programme peut également installer des composants ODBC individuels. Pour installer le Driver Manager, `SQLInstallDriverManager` un programme appelle d’abord dans l’installateur DLL pour obtenir le répertoire cible pour le driver Manager. C’est généralement l’annuaire dans lequel les reflex et les fenêtres résident. Le programme utilise ensuite l’information dans la section [ODBC Driver Manager] de l’ODBC. Fichier INF pour copier le Driver Manager et les fichiers connexes du disque d’installation à ce répertoire. Pour installer un conducteur individuel, `SQLInstallDriver` un programme appelle d’abord dans l’installateur DLL pour ajouter les spécifications du conducteur à l’ODBCINST. Fichier INI (ou le registre, sur NT). `SQLInstallDriver`retourne l’annuaire cible du conducteur — habituellement l’annuaire dans lequel les reflex windows résident. Le programme utilise ensuite l’information dans la section du conducteur de l’ODBC. Fichier INF pour copier le pilote DLL et les fichiers connexes du disque d’installation à ce répertoire.

Pour plus d’informations sur ODBC. INF, ODBCINST. INI et à l’aide de l’installateur API, voir ODBC SDK *Programmeur’s Reference,* Chapitre 19, Installation de logiciels ODBC.

## <a name="writing-an-odbc-administrator"></a><a name="_mfcnotes_writing_an_odbc_administrator"></a>Rédaction d’un administrateur ODBC

Une application de base de données MFC peut configurer et configurer les sources de données ODBC de l’une des deux façons suivantes :

- Utilisez l’administrateur de l’ODBC (disponible sous forme de programme ou d’élément de panneau de contrôle).

- Créez votre propre programme pour configurer les sources de données.

Un programme qui configure les sources de données fait des appels de fonction à l’installateur DLL. L’installateur DLL appelle une configuration DLL pour configurer une source de données. Il ya une configuration DLL pour chaque pilote; il peut s’agir du pilote DLL lui-même, ou d’un DLL séparé. La configuration DLL invite l’utilisateur pour les informations dont le pilote a besoin pour se connecter à la source de données et au traducteur par défaut, s’il est pris en charge. Il appelle ensuite l’installateur DLL et Windows API pour enregistrer ces informations dans l’ODBC. Fichier INI (ou registre).

Pour afficher une boîte de dialogue avec laquelle un utilisateur peut ajouter, modifier et supprimer les sources de données, un programme appelle `SQLManageDataSources` dans l’installateur DLL. Cette fonction est invoquée lorsque l’installateur DLL est appelé à partir du panneau de contrôle. Pour ajouter, modifier ou supprimer `SQLManageDataSources` une `ConfigDSN` source de données, les appels dans la configuration DLL pour le pilote associé à cette source de données. Pour ajouter, modifier ou supprimer directement les `SQLConfigDataSource` sources de données, un programme appelle dans l’installateur DLL. Le programme transmet le nom de la source de données et une option qui spécifie les mesures à prendre. `SQLConfigDataSource`appelle `ConfigDSN` dans la configuration DLL et `SQLConfigDataSource`lui passe les arguments de .

Pour plus d’informations, voir ODBC SDK *Programmeur’s Reference,* Chapter 23, Setup DLL Function Reference, et Chapter 24, Install DLL Function Reference.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
