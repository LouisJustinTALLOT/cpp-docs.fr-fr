---
title: 'Pages de propriétés HLSL : Fichiers de sortie'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.AssemblerOutputFile
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
ms.openlocfilehash: 6ee8042fccf2e0b635535a77d9c9a6bc68bd9999
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825299"
---
# <a name="hlsl-property-pages-output-files"></a>Pages de propriétés HLSL : Fichiers de sortie

Pour configurer les propriétés suivantes du compilateur HLSL (fxc.exe), utilisez sa propriété **Fichiers de sortie**. Pour plus d’informations sur l’accès à la **fichiers de sortie** page de propriétés dans le dossier HLSL, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

## <a name="uielement-list"></a>Liste des éléments d’interface

- **Nom de la variable dans l’en-tête**

   Spécifie le nom d’un tableau qui est utilisé pour encoder le code objet HLSL. Le tableau est contenu dans un fichier d’en-tête qui est généré par le compilateur HLSL. Le nom du fichier d’en-tête est spécifié par la propriété **Nom du fichier d’en-tête**.

Cette propriété correspond à l’argument de ligne de commande **/Vn[name]**.

- **Nom du fichier d’en-tête**

   Spécifie le nom du fichier d’en-tête qui est généré par le compilateur HLSL. L’en-tête contient le code objet HLSL qui est encodé dans un tableau. Le nom du tableau est spécifié par la propriété **Nom de la variable dans l’en-tête**.

Cette propriété correspond à l’argument de ligne de commande **/Fh[name]**.

- **Nom de fichier objet**

   Spécifie le nom du fichier objet qui est généré par le compilateur HLSL. Par défaut, la valeur est **$(OutDir)%(Filename).cso**.

Cette propriété correspond à l’argument de ligne de commande **/Fo[name]**.

- **Sortie de l’assembleur**

   **Listing du code assembleur uniquement (/Fc)** pour générer uniquement des instructions en langage assembleur. **Code de l’assembly et Hex (/Fx)** pour générer à la fois des instructions en langage assembleur et le code d’opération correspondant au format hexadécimal. Par défaut, aucune liste n’est générée.

- **Fichier de sortie de l’assembleur**

   Spécifie le nom du fichier listing d’assembly qui est généré par le compilateur HLSL.

   Cette propriété correspond aux arguments de ligne de commande **/Fc[name]** et **/Fx[name]**.

## <a name="see-also"></a>Voir aussi

[HLSL, page de propriétés](hlsl-property-pages.md)<br>
[HLSL, page de propriétés : Général](hlsl-property-pages-general.md)<br>
[HLSL, page de propriétés : Avancé](hlsl-property-pages-advanced.md)
