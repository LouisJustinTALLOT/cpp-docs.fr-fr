---
title: /INTEGRITYCHECK (Exiger la vérification de la signature)
ms.date: 11/04/2016
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
ms.openlocfilehash: 1732c612501b66753635b272f94764975c555f75
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492845"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (Exiger la vérification de la signature)

Spécifie que la signature numérique de l’image binaire doit être vérifiée au moment du chargement.

```
/INTEGRITYCHECK[:NO]
```

## <a name="remarks"></a>Notes

Par défaut, **/INTEGRITYCHECK** est désactivé.

L’option **/INTEGRITYCHECK** définit, dans l’en-tête PE du fichier dll ou du fichier exécutable, un indicateur pour que le gestionnaire de mémoire vérifie la signature numérique afin de charger l’image dans Windows. Cette option doit être définie pour les dll 32 bits et 64 bits qui implémentent le code en mode noyau chargé par certaines fonctionnalités de Windows. elle est recommandée pour tous les pilotes de périphérique sous Windows Vista, Windows 7, Windows 8, Windows Server 2008 et Windows Server 2012. Les versions de Windows antérieures à Windows Vista ignorent cet indicateur. Pour plus d’informations, consultez [signature d’intégrité forcée des fichiers exécutables portables (PE)](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le nœud **Éditeur de liens**.

1. Sélectionnez la page de propriétés **ligne de commande** .

1. Dans **options supplémentaires**, entrez `/INTEGRITYCHECK` ou `/INTEGRITYCHECK:NO`.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[Signature d’intégrité forcée des fichiers exécutables portables (PE)](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)<br/>
[Conditions requises pour la signature de code en mode noyau](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)<br/>
[DLL AppInit et démarrage sécurisé](/windows/win32/dlls/secure-boot-and-appinit-dlls)
