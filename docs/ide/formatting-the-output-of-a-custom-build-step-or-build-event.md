---
title: Mise en forme de la sortie d’une étape de build personnalisée ou d’un événement de build| Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- builds [C++], build events
- custom build steps [C++], output format
- events [C++], build
- build events [C++], output format
- build steps [C++], output format
- builds [C++], custom build steps
ms.assetid: 92ad3e38-24d7-4b89-90e6-5a16f5f998da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7da71e6391d2d3223b47ba528686d2fec003ab3a
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33321348"
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>Mise en forme de la sortie d'une étape de génération personnalisée ou d'un événement de build
Si la sortie d’un événement de build ou d’une étape de build personnalisée est correctement mise en forme, les utilisateurs bénéficient des avantages suivants :  
  
-   Les avertissements et les erreurs sont comptabilisés dans la fenêtre **Sortie**.  
  
-   La sortie apparaît dans la fenêtre **Liste des tâches**.  
  
-   Un clic sur la sortie dans la fenêtre **Sortie** permet d’afficher la rubrique appropriée.  
  
-   Les opérations F1 sont activées dans la fenêtre **Liste des tâches** ou dans la fenêtre **Sortie**.  
  
 La sortie doit avoir le format suivant :  
  
 {*filename* (*line#* [, *column#*]) &#124; *toolname*} **:**  
  
 [*any text*] {**error** &#124; **warning**} *code####***:*** localizable string*  
  
 [ *any text* ]  
  
 Où :  
  
-   {*a* &#124; *b*} correspond à un choix de *a* ou *b*.  
  
-   [`ccc`] correspond à une chaîne ou un paramètre facultatif.  
  
 Exemple :  
  
 C:\\*sourcefile.cpp*(134) : erreur C2143 : erreur de syntaxe : ';' manquant avant '}'  
  
 LINK : erreur irrécupérable LNK1104 : impossible d’ouvrir le fichier '*somelib.lib*'  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des étapes de génération personnalisée et des événements de build](../ide/understanding-custom-build-steps-and-build-events.md)