---
title: Déclenchement d’Exceptions logicielles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- run-time errors, treating as exceptions
- exception handling [C++], errors as exceptions
- exceptions [C++], flagging errors as exceptions
- errors [C++], treating as exceptions
- exception handling [C++], detecting errors
- structured exception handling [C++], errors as exceptions
- exceptions [C++], software
- RaiseException function
- software exceptions [C++]
- formats [C++], exception codes
ms.assetid: be1376c3-c46a-4f52-ad1d-c2362840746a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75f882fe924ba825a5f3ec641a98175104635e92
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085811"
---
# <a name="raising-software-exceptions"></a>Déclenchement d'exceptions logicielles

Certaines des sources les plus courantes d'erreurs de programme ne sont pas marquées en tant qu'exceptions par le système. Par exemple, si vous essayez d'allouer un bloc de mémoire mais que la mémoire disponible est insuffisante, la fonction runtime ou API ne déclenche pas d'exception mais retourne un code d'erreur.

Toutefois, vous pouvez traiter n’importe quelle condition en tant qu’exception en détectant cette condition dans votre code, puis les rapports en appelant le [RaiseException](https://msdn.microsoft.com/library/windows/desktop/ms680552) (fonction). Le fait de marquer les erreurs de cette manière vous permet de tirer parti de la gestion structurée des exceptions pour tout type d'erreur d'exécution.

Pour utiliser la gestion structurée des exceptions avec des erreurs :

- Définissez votre propre code d'exception pour l'événement.

- Appelez `RaiseException` lorsque vous détectez un problème.

- Utilisez les filtres de gestion des exceptions pour tester le code d'exception que vous avez défini.

Le \<winerror.h > fichier illustre le format pour les codes d’exception. Pour veiller à ne pas définir un code qui est en conflit avec un code d'exception existant, définissez le troisième bit le plus significatif à 1. Les quatre bits les plus significatifs doivent être définis comme indiqué dans le tableau suivant.

|Bits|Paramètre binaire recommandé|Description|
|----------|--------------------------------|-----------------|
|31-30|11|Ces deux bits décrivent l'état de base du code : 11 = erreur, 00 = succès, 01 = informatif, 10 = avertissement.|
|29|1|Bit client. Affectez-lui la valeur 1 pour les codes définis par l'utilisateur.|
|28|0|Bit réservé. (Laissez la valeur 0.)|

Vous pouvez définir les deux premiers bits à un paramètre autre 11 binaire, bien que le paramètre « erreur » soit appropriée pour la plupart des exceptions. Veillez à définir les bits 29 et 28 comme indiqué dans le tableau précédent.

Le code d’erreur résultant doit donc contenir les quatre bits le plus élevés défini sur la valeur e hexadécimale. Par exemple, les définitions suivantes définissent les codes d’exception qui ne pas en conflit avec les codes d’exception Windows. (Toutefois, vous pouvez être amené à vérifier quels codes sont utilisés par les DLL tierces.)

```cpp
#define STATUS_INSUFFICIENT_MEM       0xE0000001
#define STATUS_FILE_BAD_FORMAT        0xE0000002
```

Après avoir défini un code d'exception, vous pouvez l'utiliser pour lever une exception. Par exemple, le code suivant déclenche le `STATUS_INSUFFICIENT_MEM` exception en réponse à un problème d’allocation de mémoire :

```cpp
lpstr = _malloc( nBufferSize );
if (lpstr == NULL)
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);
```

Si vous souhaitez déclencher simplement une exception, vous pouvez définir les trois derniers paramètres à 0. Les trois derniers paramètres sont utiles pour transmettre des informations supplémentaires et définir un indicateur qui empêche les gestionnaires de poursuivre l'exécution. Consultez le [RaiseException](https://msdn.microsoft.com/library/windows/desktop/ms680552) fonction dans le SDK Windows pour plus d’informations.

Dans vos filtres de gestion des exceptions, vous pouvez ensuite tester les codes que vous avez définis. Exemple :

```cpp
__try {
    ...
}
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )
```

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)<br/>
[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)