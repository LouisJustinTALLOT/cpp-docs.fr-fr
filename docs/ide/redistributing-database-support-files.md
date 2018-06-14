---
title: Redistribution de fichiers de prise en charge de base de données | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- redistributing database support files
- database support files [C++], redistributing
ms.assetid: d80cffe0-177c-4515-9de7-fbf0517eb8d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a51697367480569e2d27a4cb67791f5fe4d39a8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323873"
---
# <a name="redistributing-database-support-files"></a>Redistribution de fichiers de prise en charge de base de données
Vous pouvez redistribuer des fichiers de prise en charge pour les objets d’accès aux données (DAO) et pour les technologies de bases de données se trouvant dans le kit SDK Microsoft Data Access.  
  
## <a name="installing-dao-support-files"></a>Installation de fichiers de prise en charge DAO  
 Pour obtenir la version la plus récente de DAO, consultez [l’article 239114 pour savoir comment obtenir le dernier Service Pack pour le moteur de base de données Microsoft Jet 4.0](http://go.microsoft.com/fwlink/p/?linkid=198014) sur le site web du support technique Microsoft.  
  
## <a name="installing-microsoft-data-access-sdk-support-files"></a>Installation de fichiers de prise en charge du kit SDK Microsoft Data Access  
 Utilisez Mdac_typ.exe pour installer la prise en charge ODBC, OLE DB, ADO (ActiveX Data Objects) et RDS (Remote Data Services). Mdac_typ.exe est situé dans le dossier ..\WCU\MDAC28\ sur le support d’installation Visual Studio. Vous pouvez également télécharger Mdac_typ.exe à partir du site web [Centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/p/?linkid=198015).  
  
 Pour plus d’informations, sur le site web [MSDN](http://go.microsoft.com/fwlink/p/?linkid=198016), recherchez « redistribution MDAC 2.8 SP1 ». Si vous utilisez des projets d’installation Visual Studio pour déployer votre application, consultez [Déploiement et dépendances](http://msdn.microsoft.com/en-us/49e9b84d-bd6a-4388-b9ac-46ea79cf0733).  
  
## <a name="see-also"></a>Voir aussi  
 [Redistribution des fichiers Visual C++](../ide/redistributing-visual-cpp-files.md)