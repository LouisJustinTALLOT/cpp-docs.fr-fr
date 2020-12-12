---
description: En savoir plus sur:/CLRUNMANAGEDCODECHECK (supprimer SuppressUnmanagedCodeSecurityAttribute)
title: /CLRUNMANAGEDCODECHECK (Supprimer SuppressUnmanagedCodeSecurityAttribute)
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.openlocfilehash: e08b7b4b18a463122316b041ad81d6ddd2598bca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182396"
---
# <a name="clrunmanagedcodecheck-remove-suppressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK (Supprimer SuppressUnmanagedCodeSecurityAttribute)

**/CLRUNMANAGEDCODECHECK** spécifie que l’éditeur de liens n’applique pas <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> aux appels `PInvoke` générés par l’éditeur de liens à partir du code managé dans des DLL natives.

## <a name="syntax"></a>Syntaxe

> **/CLRUNMANAGEDCODECHECK**[**:NO**]

## <a name="remarks"></a>Notes

Par défaut, l’éditeur de liens applique **SuppressUnmanagedCodeSecurityAttribute** aux appels `PInvoke` générés par l’éditeur de liens. Lorsque **/CLRUNMANAGEDCODECHECK** est en vigueur, **SuppressUnmanagedCodeSecurityAttribute** est supprimé. Pour appliquer explicitement **SuppressUnmanagedCodeSecurityAttribute** aux appels `PInvoke` générés par l’éditeur de liens, vous pouvez utiliser **/CLRUNMANAGEDCODECHECK:NO**.

L’éditeur de liens ajoute seulement l’attribut aux objets qui sont compilés à l’aide de **/clr** ou **/clr:pure**. Toutefois, l’option de compilateur **/clr:pure** est dépréciée dans Visual Studio 2015 et non prise en charge dans Visual Studio 2017 et ultérieur.

Un appel `PInvoke` est généré par l’éditeur de liens quand celui-ci ne peut pas détecter de symbole managé pour répondre à une référence à partir d’un appelant managé, mais peut trouver un symbole natif pour cette référence. Pour plus d’informations sur `PInvoke`, consultez [Appel à des fonctions natives à partir de code managé](../../dotnet/calling-native-functions-from-managed-code.md).

Notez que si vous utilisez <xref:System.Security.AllowPartiallyTrustedCallersAttribute> dans votre code, vous devez définir explicitement **/CLRUNMANAGEDCODECHECK** pour supprimer l’attribut **SuppressUnmanagedCodeSecurity**. Il existe une faille de sécurité potentielle si une image contient à la fois les attributs **SuppressUnmanagedCodeSecurity** et **AllowPartiallyTrustedCallers**.

Consultez [Instructions de codage sécurisé pour le code non managé](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code) pour plus d’informations sur les conséquences de l’utilisation de **SuppressUnmanagedCodeSecurityAttribute**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le nœud **Éditeur de liens**.

1. Sélectionnez la page de propriétés **Avancé**.

1. Modifiez la propriété **Vérification du code non managé CLR**.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
