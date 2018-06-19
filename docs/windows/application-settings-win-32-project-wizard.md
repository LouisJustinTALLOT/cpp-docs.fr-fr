---
title: Paramètres de l’application, Assistant projet Win 32 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.appwiz.win32.appset
dev_langs:
- C++
helpviewer_keywords:
- application settings [C++]
- Win32 Project Wizard, application settings
ms.assetid: d6b818f0-9b23-4793-a6c5-df1c8c594bad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 55ae50d849a67da69cde6a9c4b1529c34ee4b428
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860058"
---
# <a name="application-settings-win-32-project-wizard"></a>Paramètres de l'application, Assistant Projet Win 32
Utilisez cette page de l’Assistant pour définir les options du projet Win32.  
  
 **Type d’application**  
 Crée le type d’application spécifié.  
  
|Option|Description|  
|------------|-----------------|  
|**Application console**|Crée une application console. Programmes de console sont développés avec [fonctions de la Console](https://msdn.microsoft.com/en-us/library/ms813137.aspx), qui prennent en charge en mode caractères dans les fenêtres de console. Visual C++ [bibliothèques](../c-runtime-library/c-run-time-library-reference.md) également fournir la sortie et d’entrée à partir des fenêtres de console avec des fonctions d’e/s standard, telles que **printf_s()** et **scanf_s()**. Une application console ne comporte aucune interface utilisateur graphique. Il compile en un fichier .exe et peut être exécuté comme une application autonome à partir de la ligne de commande.<br /><br /> Vous pouvez ajouter la prise en charge de MFC et ATL à une application console.|  
|**Application Windows**|Crée un programme Win32. Un programme Win32 est une application exécutable (EXE) écrite en C ou C++, à l’aide d’appels à l’API Win32 pour créer une interface utilisateur graphique.<br /><br /> Vous ne pouvez pas ajouter MFC ou ATL prend en charge pour une application Windows.|  
|**DLL**|Crée une bibliothèque de liens dynamiques (DLL) Win32. Une DLL Win32 est un fichier binaire, écrit en C ou C++, qui utilise des appels à l’API Win32 plutôt qu’à des classes MFC et qui agit comme une bibliothèque partagée de fonctions qui peuvent être utilisés simultanément par plusieurs applications.<br /><br /> Vous ne pouvez pas ajouter MFC ou ATL prend en charge pour une application de la DLL. Vous pouvez indiquer que la DLL exporte des symboles.|  
|**Bibliothèque statique**|Crée une bibliothèque statique. Une bibliothèque statique est un fichier contenant des objets et leurs fonctions et les données qui est lié à votre programme lorsque le fichier exécutable est généré. Cette rubrique explique comment créer les fichiers de démarrage et [propriétés de projet](../ide/property-pages-visual-cpp.md) pour une bibliothèque statique. Un fichier de bibliothèque statique offre les avantages suivants :<br /><br /> -Une bibliothèque statique Win32 est utile si l’application que vous travaillez effectue des appels à l’API Win32 plutôt qu’à des classes MFC.<br />-Le processus de liaison est le même si le reste de votre application Windows est écrit en C ou c++.<br />-Vous pouvez lier une bibliothèque statique à un programme MFC ou à un programme non MFC.|  
  
 **Options supplémentaires**  
 Définit la prise en charge et les options de l’application, en fonction de son type.  
  
|Option|Description|  
|------------|-----------------|  
|**Projet vide**|Spécifie que les fichiers projet sont vides. Si vous avez un ensemble de fichiers de code source (par exemple, les fichiers .cpp, fichiers d’en-tête, icônes, barres d’outils, boîtes de dialogue et ainsi de suite) et que vous souhaitez créer un projet dans l’environnement de développement Visual C++, vous devez d’abord créer un projet vide, puis ajoutez les fichiers au projet.<br /><br /> Cette sélection n’est pas disponible pour les projets de bibliothèque statique.|  
|**Symboles d’exportation**|Spécifie que le projet de DLL exporte des symboles.|  
|**En-tête précompilé**|Spécifie que le projet de bibliothèque statique utilise un en-tête précompilé.|  
|Vérifie de cycle de vie de développement de sécurité (SDL)|Pour plus d’informations sur SDL, consultez [Guide de processus du cycle de vie de développement de sécurité Microsoft (SDL)](../build/reference/sdl-enable-additional-security-checks.md)|  
  
 **Ajouter la prise en charge pour**  
 Ajouter la prise en charge pour l’une des bibliothèques fournies dans Visual C++.  
  
|Option|Description|  
|------------|-----------------|  
|**ATL**|Intègre la prise en charge de projet pour les classes dans la bibliothèque ATL (Active Template). Pour les applications console Win32 uniquement.<br /><br /> **Remarque** cette option n’indique pas de prise en charge pour l’ajout d’objets ATL à l’aide de la bibliothèque ATL Assistants de code. Vous pouvez ajouter des objets ATL qu’aux projets ATL ou MFC des projets avec ATL prennent en charge.|  
|**MFC**|Intègre la prise en charge de projet pour la bibliothèque Microsoft Foundation classes (MFC). Pour les applications console Win32 et des bibliothèques statiques.|  
  
## <a name="see-also"></a>Voir aussi  
 [Application Win32 (Assistant)](../windows/win32-application-wizard.md)   
