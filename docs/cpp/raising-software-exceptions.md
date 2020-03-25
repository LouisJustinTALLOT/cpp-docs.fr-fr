---
title: Déclenchement d'exceptions logicielles
ms.date: 11/04/2016
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
ms.openlocfilehash: f50d84bd034cc6eeb00dc17cb3b7272a988b6731
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179131"
---
# <a name="raising-software-exceptions"></a>Déclenchement d'exceptions logicielles

Certaines des sources les plus courantes d'erreurs de programme ne sont pas marquées en tant qu'exceptions par le système. Par exemple, si vous essayez d'allouer un bloc de mémoire mais que la mémoire disponible est insuffisante, la fonction runtime ou API ne déclenche pas d'exception mais retourne un code d'erreur.

Toutefois, vous pouvez traiter n’importe quelle condition comme une exception en détectant cette condition dans votre code, puis en la signalant en appelant la fonction [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception) . Le fait de marquer les erreurs de cette manière vous permet de tirer parti de la gestion structurée des exceptions pour tout type d'erreur d'exécution.

Pour utiliser la gestion structurée des exceptions avec des erreurs :

- Définissez votre propre code d'exception pour l'événement.

- Appelez `RaiseException` lorsque vous détectez un problème.

- Utilisez les filtres de gestion des exceptions pour tester le code d'exception que vous avez défini.

Le \<le fichier winerror. h > affiche le format des codes d’exception. Pour veiller à ne pas définir un code qui est en conflit avec un code d'exception existant, définissez le troisième bit le plus significatif à 1. Les quatre bits les plus significatifs doivent être définis comme indiqué dans le tableau suivant.

|Bits|Paramètre binaire recommandé|Description|
|----------|--------------------------------|-----------------|
|31-30|11|Ces deux bits décrivent l'état de base du code : 11 = erreur, 00 = succès, 01 = informatif, 10 = avertissement.|
|29|1|Bit client. Affectez-lui la valeur 1 pour les codes définis par l'utilisateur.|
|28|0|Bit réservé. (Laissez la valeur 0.)|

Vous pouvez définir les deux premiers bits à un paramètre autre 11 binaire, bien que le paramètre « erreur » soit appropriée pour la plupart des exceptions. Veillez à définir les bits 29 et 28 comme indiqué dans le tableau précédent.

Le code d’erreur obtenu doit donc avoir les quatre bits les plus élevés définis sur E hexadécimale. Par exemple, les définitions suivantes définissent des codes d’exception qui ne sont pas en conflit avec les codes d’exception Windows. (Toutefois, vous pouvez être amené à vérifier quels codes sont utilisés par les DLL tierces.)

```cpp
#define STATUS_INSUFFICIENT_MEM       0xE0000001
#define STATUS_FILE_BAD_FORMAT        0xE0000002
```

Après avoir défini un code d'exception, vous pouvez l'utiliser pour lever une exception. Par exemple, le code suivant déclenche l’exception `STATUS_INSUFFICIENT_MEM` en réponse à un problème d’allocation de mémoire :

```cpp
lpstr = _malloc( nBufferSize );
if (lpstr == NULL)
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);
```

Si vous souhaitez déclencher simplement une exception, vous pouvez définir les trois derniers paramètres à 0. Les trois derniers paramètres sont utiles pour transmettre des informations supplémentaires et définir un indicateur qui empêche les gestionnaires de poursuivre l'exécution. Pour plus d’informations, consultez la fonction [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception) dans la SDK Windows.

Dans vos filtres de gestion des exceptions, vous pouvez ensuite tester les codes que vous avez définis. Par exemple :

```cpp
__try {
    ...
}
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )
```

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)<br/>
[Gestion structurée des exceptions (C++C/)](../cpp/structured-exception-handling-c-cpp.md)
