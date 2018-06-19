---
title: -DEBUGTYPE (Options d’informations de débogage) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /debugtype
dev_langs:
- C++
helpviewer_keywords:
- /DEBUGTYPE linker option
- DEBUGTYPE linker option
- -DEBUGTYPE linker option
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66868f7648d20b890f3c1e8c40802d77e3af4544
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375368"
---
# <a name="debugtype-debug-info-options"></a>/DEBUGTYPE (options d'informations de débogage)
L'option /DEBUGTYPE spécifie les types d'informations de débogage générées par l'option /DEBUG.  
  
```  
/DEBUGTYPE:[CV | PDATA | FIXUP]  
```  
  
## <a name="arguments"></a>Arguments  
 CV  
 Indique à l'éditeur de liens d'émettre des informations de débogage pour les symboles, les numéros de ligne et d'autres informations de compilation d'objet dans le fichier PDB. Par défaut, cette option est activée lorsque **/DEBUG** est spécifié et **/Debug.** n’est pas spécifié.  
  
 PDATA  
 Indique à l'éditeur de liens d'ajouter des entrées .pdata et .xdata aux informations de flux de débogage dans le fichier PDB. Par défaut, cette option est activée lorsqu’à la fois le **/DEBUG** et **c** options sont spécifiées. Si **/DEBUGTYPE:PDATA** est spécifié par lui-même, l’éditeur de liens inclut automatiquement les symboles de débogage dans le fichier PDB. Si **/DEBUGTYPE:PDATA, correction** est spécifié, l’éditeur de liens n’inclut pas de symboles de débogage dans le fichier PDB.  
  
 FIXUP  
 Indique à l'éditeur de liens d'ajouter des entrées de table de réadressage aux informations de flux de débogage dans le fichier PDB. Par défaut, cette option est activée lorsqu’à la fois le **/DEBUG** et **/PROFILE** options sont spécifiées. Si **/DEBUGTYPE:FIXUP** ou **/DEBUGTYPE:FIXUP, PDATA** est spécifié, l’éditeur de liens n’inclut pas de symboles de débogage dans le fichier PDB.  
  
 Arguments à **/Debug.** peuvent être combinés dans n’importe quel ordre, en les séparant par une virgule. Le **/Debug.** option et ses arguments ne sont pas respecter la casse.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **/Debug.** option pour spécifier l’inclusion de réadressage table données ou .pdata et .xdata informations d’en-tête dans le flux de débogage. Par conséquent, l'éditeur de liens inclut des informations concernant le code en mode utilisateur qui est visible dans un débogueur du noyau lors de la séparation de code en mode noyau. Pour rendre les symboles de débogage disponibles quand **correction** est spécifié, incluez le **CV** argument.  
  
 Pour déboguer le code en mode utilisateur, qui est généralement utilisé pour les applications, les **/Debug.** option n’est pas nécessaire. Par défaut, les commutateurs de compilation qui spécifient le débogage de sortie ([/Z7, / Zi, /ZI](../../build/reference/z7-zi-zi-debug-information-format.md)) toutes les informations requièrent par Visual Studio du débogueur émettre. Utilisez **/DEBUGTYPE:PDATA** ou **/DEBUGTYPE : CV, PDATA, correction** pour déboguer le code qui combine des composants en mode utilisateur et en mode noyau, par exemple une application de configuration pour un pilote de périphérique. Pour plus d’informations sur les débogueurs en mode noyau, consultez [outils de débogage pour Windows (WinDbg, KD, CDB, NTSD)](http://go.microsoft.com/fwlink/p?LinkID=285651)  
  
## <a name="see-also"></a>Voir aussi  
 [/Debug (générer les informations de débogage)](../../build/reference/debug-generate-debug-info.md)   
 [/Driver (pilote Windows NT en Mode noyau)](../../build/reference/driver-windows-nt-kernel-mode-driver.md)   
 [/Profile (profileur des outils performances)](../../build/reference/profile-performance-tools-profiler.md)   
 [Outils de débogage pour Windows (WinDbg, KD, CDB, NTSD)](http://go.microsoft.com/fwlink/p?LinkID=285651)