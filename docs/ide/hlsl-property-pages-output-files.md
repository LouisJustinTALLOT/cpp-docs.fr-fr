---
title: 'Pages de propriétés HLSL : Fichiers de sortie | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.AssemblerOutputFile
dev_langs:
- C++
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4fd1dc3ba92201567f24aa84ff8dddcd96798b38
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33339194"
---
# <a name="hlsl-property-pages-output-files"></a>Pages de propriétés HLSL : fichiers de sortie
Pour configurer les propriétés suivantes du compilateur HLSL (fxc.exe), utilisez sa propriété **Fichiers de sortie**. Pour plus d’informations sur l’accès à la page de propriétés **Fichiers de sortie** dans le dossier HLSL, consultez [Utilisation des propriétés de projet](../ide/working-with-project-properties.md).  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Nom de la variable dans l’en-tête**  
 Spécifie le nom d’un tableau qui est utilisé pour encoder le code objet HLSL. Le tableau est contenu dans un fichier d’en-tête qui est généré par le compilateur HLSL. Le nom du fichier d’en-tête est spécifié par la propriété **Nom du fichier d’en-tête**.  
  
 Cette propriété correspond à l’argument de ligne de commande **/Vn[name]**.  
  
 **Nom du fichier d’en-tête**  
 Spécifie le nom du fichier d’en-tête qui est généré par le compilateur HLSL. L’en-tête contient le code objet HLSL qui est encodé dans un tableau. Le nom du tableau est spécifié par la propriété **Nom de la variable dans l’en-tête**.  
  
 Cette propriété correspond à l’argument de ligne de commande **/Fh[name]**.  
  
 **Nom de fichier objet**  
 Spécifie le nom du fichier objet qui est généré par le compilateur HLSL. Par défaut, la valeur est **$(OutDir)%(Filename).cso**.  
  
 Cette propriété correspond à l’argument de ligne de commande **/Fo[name]**.  
  
 **Sortie de l’assembleur**  
 **Listing du code assembleur uniquement (/Fc)** pour générer uniquement des instructions en langage assembleur. **Code de l’assembly et Hex (/Fx)** pour générer à la fois des instructions en langage assembleur et le code d’opération correspondant au format hexadécimal. Par défaut, aucune liste n’est générée.  
  
 **Fichier de sortie de l’assembleur**  
 Spécifie le nom du fichier listing d’assembly qui est généré par le compilateur HLSL.  
  
 Cette propriété correspond aux arguments de ligne de commande **/Fc[name]** et **/Fx[name]**.  
  
## <a name="see-also"></a>Voir aussi  
 [HLSL, page de propriétés](../ide/hlsl-property-pages.md)   
 [Pages de propriétés HLSL : Général](../ide/hlsl-property-pages-general.md)   
 [HLSL, page de propriétés : Avancé](../ide/hlsl-property-pages-advanced.md)