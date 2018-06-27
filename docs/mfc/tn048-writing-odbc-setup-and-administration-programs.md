---
title: 'TN048 : Écriture ODBC programmes d’installation et Administration pour les Applications de base de données MFC | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.odbc
dev_langs:
- C++
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7d89b6c6e05a5baf973abace2c64de3b52754f5
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954554"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048 : écriture de programmes d'installation et d'administration ODBC pour les applications de base de données MFC
> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.  
  
 Applications à l’aide des classes de base de données MFC devez un programme d’installation qui installe les composants ODBC. Ils ont également besoin d’un programme d’Administration ODBC qui Récupère des informations sur les pilotes disponibles, pour spécifier les pilotes par défaut et pour configurer des sources de données. Cette note décrit l’utilisation de l’API du programme d’installation de ODBC pour ces programmes d’écriture.  
  
##  <a name="_mfcnotes_writing_an_odbc_setup_program"></a> Écriture d’un programme d’installation ODBC  
 Une application de base de données MFC requiert le Gestionnaire de pilotes ODBC (ODBC. DLL) et des pilotes ODBC pour pouvoir accéder à des sources de données. Nombre de pilotes ODBC requièrent également des DLL de communication et de réseau supplémentaires. La plupart des pilotes ODBC fournis avec un programme d’installation installera les composants ODBC requis. Les développeurs d’applications à l’aide des classes de base de données MFC peuvent :  
  
-   S’appuient sur les programmes spécifiques au pilote le programme d’installation pour l’installation des composants ODBC. Cette opération exige aucun autre travail sur le développeur, vous pouvez redistribuer simplement du programme d’installation du pilote.  
  
-   Vous pouvez également écrire votre propre programme d’installation qui va installer le Gestionnaire de pilotes et le pilote.  
  
 L’API du programme d’installation ODBC peut être utilisé pour écrire des programmes d’installation d’application spécifique. Les fonctions dans le programme d’installation API sont implémentées par le programme d’installation ODBC DLL — ODBCINST. DLL sur Windows 16 bits et ODBCCP32. DLL sur Win32. Une application peut appeler `SQLInstallODBC` dans le programme d’installation DLL, qui va installer le Gestionnaire de pilotes ODBC et les pilotes ODBC requis traducteurs. Il enregistre ensuite les pilotes installés et les traducteurs dans ODBCINST. Fichier INI (ou le Registre, sous NT). `SQLInstallODBC` nécessite le chemin d’accès complet à ODBC. Fichier INF, qui contient la liste des pilotes à installer et décrit les fichiers qui composent chaque pilote. Il contient également des informations similaires sur le Gestionnaire de pilotes et les convertisseurs. ODBC. Les fichiers INF sont généralement fournis par les développeurs de pilote.  
  
 Un programme peut également installer les composants ODBC individuels. Pour installer le Gestionnaire de pilotes, un programme appelle tout d’abord `SQLInstallDriverManager` dans le programme d’installation de la DLL pour obtenir le répertoire cible pour le Gestionnaire de pilotes. Il s’agit généralement du répertoire dans lesquels résident les DLL Windows. Le programme utilise ensuite les informations dans la section [Gestionnaire de pilotes ODBC] de ODBC. Fichier INF pour copier le Gestionnaire de pilotes et les fichiers associés à partir du disque d’installation dans ce répertoire. Pour installer un pilote individuel, un programme appelle tout d’abord `SQLInstallDriver` dans le programme d’installation du fichier DLL pour ajouter la spécification de pilote à ODBCINST. Fichier INI (ou le Registre, sous NT). `SQLInstallDriver` Retourne le répertoire du pilote cible, généralement dans le répertoire dans lequel résident les DLL Windows. Le programme utilise ensuite les informations dans la section du pilote ODBC. Fichier INF pour copier la DLL du pilote et les fichiers associés à partir du disque d’installation dans ce répertoire.  
  
 Pour plus d’informations sur ODBC. INF, ODBCINST. INI et à l’aide du programme d’installation de l’API, consultez ODBC SDK *de référence du programmeur,* chapitre 19, l’installation des logiciels ODBC.  
  
##  <a name="_mfcnotes_writing_an_odbc_administrator"></a> L’écriture d’un administrateur ODBC  
 Une application de base de données MFC permettre installer et configurer des sources de données ODBC dans un des deux manières, comme suit :  
  
-   Utilisez l’administrateur ODBC (disponible comme un programme ou un élément du Panneau de configuration).  
  
-   Créer votre propre programme pour configurer des sources de données.  
  
 Un programme qui configure les sources de données effectue des appels de fonction à la DLL de programme d’installation. Le programme d’installation DLL appelle une DLL pour configurer une source de données de configuration. Il existe une configuration de DLL pour chaque pilote ; Il peut être la DLL du pilote ou une DLL distincte. La DLL d’installation invite l’utilisateur pour plus d’informations que le pilote doit se connecter à la source de données et le convertisseur par défaut, si pris en charge. Il appelle ensuite le programme d’installation DLL et les API Windows pour enregistrer ces informations dans ODBC. Fichier INI (ou Registre).  
  
 Pour afficher une boîte de dialogue avec laquelle un utilisateur peut ajouter, modifier et supprimer des sources de données, un programme appelle `SQLManageDataSources` dans la DLL de programme d’installation. Cette fonction est appelée lorsque le programme d’installation DLL est appelée à partir du panneau. Pour ajouter, modifier ou supprimer une source de données, `SQLManageDataSources` appelle `ConfigDSN` dans la DLL d’installation pour le pilote associé à cette source de données. Pour ajouter, modifier ou supprimer des données directement sources, les appels d’un programme `SQLConfigDataSource` dans le programme d’installation DLL. Le programme transmet le nom de la source de données et une option qui spécifie l’action à entreprendre. `SQLConfigDataSource` appels `ConfigDSN` dans la DLL d’installation et transmet les arguments de `SQLConfigDataSource`.  
  
 Pour plus d’informations, consultez ODBC SDK *de référence du programmeur,* chapitre 23, référence des fonctions DLL le programme d’installation et chapitre 24, référence de fonction DLL de programme d’installation.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

