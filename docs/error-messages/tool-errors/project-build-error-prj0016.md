---
title: Erreur de génération PRJ0016 de projet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0016
dev_langs:
- C++
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c07de9e766b7c2126d0ce4c8d1daed631a8355c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194738"
---
# <a name="project-build-error-prj0016"></a>Erreur de génération de projet PRJ0016
Les paramètres de sécurité utilisateur empêchent la création du processus. Ces paramètres sont requis pour la génération.  
  
 Vous êtes connecté en tant qu’utilisateur qui ne dispose pas des autorisations nécessaires pour créer des processus à l’aide d’un processus. Vous devez modifier les niveaux d’autorisation pour ce compte d’utilisateur, ou contactez votre administrateur de compte.  
  
 Cette erreur peut également se produire si la valeur de la clé de Registre suivante :  
  
 \\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun  
  
 Pour résoudre cette erreur, supprimez la clé RestrictRun. Si cette clé de Registre est nécessaire, ajoutez **vcspawn.exe** à la liste des entrées dans la clé.  
  
 Une autre cause de cette erreur est que votre paramètre de stratégie n’inclut pas VCSpawn.exe sous la clé de Registre HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun comme programme Windows autorisé pour ce compte d’utilisateur.  
  
 Pour plus d’informations, consultez :  
  
-   Base de connaissances l’article 324153, qui est disponible sur [ http://support.microsoft.com/default.aspx?scid=kb; en-us ; 324153](http://support.microsoft.com/default.aspx?scid=kb;en-us;324153).  
  
-   [Respect des paramètres de stratégie système](https://msdn.microsoft.com/library/aa372139), la section sur « Exécuter uniquement Windows applications autorisées ».