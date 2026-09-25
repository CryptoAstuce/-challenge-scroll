# challenge-scroll

Solution du **0x Challenge on Scroll** : échange WETH → wstETH via l'API 0x Swap et Permit2, avec affichage des sources de liquidité, des taxes de tokens et de la monétisation (frais d'affiliation, collecte du surplus).

## Contenu

| Fichier | Rôle |
| --- | --- |
| `index.ts` | Script principal : sources de liquidité sur Scroll, prix et cotation 0x, signature Permit2, envoi de la transaction. |
| `abi/weth-abi.ts` | ABI du contrat WETH9 utilisé par `index.ts`. |
| `ERC20.sol` | Token ERC-20 d'exemple (`TONCONTRAT`, hérité d'OpenZeppelin, aplati). |
| `TokenSwapSimple` | Contrat `SimpleTokenSwap` aplati, qui délègue l'échange à un routeur compatible Uniswap V3. |

## Utilisation

```bash
npm install
cp .env.example .env   # renseigner les variables ci-dessous
npm start              # équivaut à: npx tsx index.ts
```

| Variable | Description |
| --- | --- |
| `PRIVATE_KEY` | Clé privée du compte, sans le préfixe `0x`. |
| `ZERO_EX_API_KEY` | Clé d'API 0x. |
| `ALCHEMY_HTTP_TRANSPORT_URL` | URL RPC HTTP pour Scroll. |

> Ne jamais committer de clé privée ni de fichier `.env`. Utiliser un compte de test : le script envoie une vraie transaction.

`npm run typecheck` vérifie le typage (`tsc --noEmit`).

## Licence

Le code hérité (OpenZeppelin, interfaces Uniswap) conserve sa licence MIT d'origine, indiquée en tête des fichiers concernés.
