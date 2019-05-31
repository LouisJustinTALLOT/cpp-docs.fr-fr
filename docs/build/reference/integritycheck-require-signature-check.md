---
title: /INTEGRITYCHECK (Exiger la vérification de la signature)
ms.date: 11/04/2016
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
ms.openlocfilehash: a46f31140c01753fdaa6e72fd0f741f569a5ad94
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450447"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (Exiger la vérification de la signature)

Spécifie que la signature numérique de l’image binaire doit être vérifiée au moment du chargement.

```
/INTEGRITYCHECK[:NO]
```

## <a name="remarks"></a>Notes

Par défaut, **/INTEGRITYCHECK** est désactivé.

Le **/INTEGRITYCHECK** groupes d’options, dans l’en-tête PE du fichier DLL ou du fichier exécutable, un indicateur pour le Gestionnaire de mémoire vérifier une signature numérique afin de charger l’image dans Windows. Cette option doit être définie pour les DLL 32 bits et 64 bits qui implémentent le code en mode noyau chargé par certaines fonctionnalités de Windows et est recommandée pour tous les pilotes de périphériques sur Windows Vista, Windows 7, Windows 8, Windows Server 2008 et Windows Server 2012. Les versions de Windows antérieures à Windows Vista ignorent cet indicateur. Pour plus d’informations, consultez [forcé l’intégrité de signature de fichiers Portable Executable (PE)](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le nœud **Éditeur de liens**.

1. Sélectionnez le **ligne de commande** page de propriétés.

1. Dans **des Options supplémentaires**, entrez `/INTEGRITYCHECK` ou `/INTEGRITYCHECK:NO`.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[Forcé l’intégrité signature de fichiers Portable Executable (PE)](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)<br/>
[Procédure pas à pas de signature du Code en Mode noyau](https://msdn.microsoft.com/windows/hardware/gg487328.aspx)<br/>
[DLL AppInit dans Windows 7 et Windows Server 2008](https://msdn.microsoft.com/windows/hardware/gg463040.aspx)
