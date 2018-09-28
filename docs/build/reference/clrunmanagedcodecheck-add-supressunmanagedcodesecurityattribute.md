---
title: /CLRUNMANAGEDCODECHECK (ajouter SuppressUnmanagedCodeSecurityAttribute) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
dev_langs:
- C++
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 679adc527cc70056e1292eb7e639499bd814bca6
ms.sourcegitcommit: 7838764e09819822a105accf5d773b2e37ffa0ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47429759"
---
# <a name="clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK (ajouter SuppressUnmanagedCodeSecurityAttribute)

**/CLRUNMANAGEDCODECHECK** Spécifie si l’éditeur de liens applique <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> généré à l’éditeur de liens `PInvoke` appelle du code managé dans des DLL natives.

## <a name="syntax"></a>Syntaxe

> **/CLRUNMANAGEDCODECHECK**[**: NO**]

## <a name="remarks"></a>Notes

Par défaut, l’éditeur de liens applique le **SuppressUnmanagedCodeSecurityAttribute** généré à l’éditeur de liens `PInvoke` appels. Lorsque **/CLRUNMANAGEDCODECHECK** est en effet, **SuppressUnmanagedCodeSecurityAttribute** n’est pas appliqué.

L’éditeur de liens ajoute seulement l’attribut aux objets compilés avec **/CLR** ou **/CLR : pure**. Toutefois, le **/CLR : pure** option du compilateur est déconseillée dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Un `PInvoke` appel est généré par l’éditeur de liens lors de l’éditeur de liens ne peut pas détecter de symbole managé pour répondre à une référence à partir d’un appelant managé, mais peut rechercher un symbole natif correspondant à cette référence. Pour plus d’informations sur `PInvoke`, consultez [appelant des fonctions natives à partir de Code managé](../../dotnet/calling-native-functions-from-managed-code.md).

Notez que si vous utilisez <xref:System.Security.AllowPartiallyTrustedCallersAttribute> dans votre code, vous devez définir explicitement **/CLRUNMANAGEDCODECHECK**. Il est une faille de sécurité potentielle si une image contient à la fois les attributs SuppressUnmanagedCodeSecurity et AllowPartiallyTrustedCallers.

Consultez [instructions de codage sécurisé pour le Code non managé](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code) pour plus d’informations sur les conséquences de l’utilisation de **SuppressUnmanagedCodeSecurityAttribute**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le **l’éditeur de liens** nœud.

1. Sélectionnez le **avancé** page de propriétés.

1. Modifier le **vérification du Code non managé CLR** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>.

## <a name="see-also"></a>Voir aussi

- [Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)
- [Options de l’éditeur de liens](../../build/reference/linker-options.md)
