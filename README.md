# MoarCoin

POW/POS mineable cryptocurrency with Masternodes, based on a secure C11 algorithm.

## Main futures:

*	ASIC Resistance
*	NiceHash Resistance
*	Nvidia & AMD GPU Mining
*	Instamine Protection
*	Wallet Built-in Block Explorer
*	Masternode Reward Protection
*	Friendly Masternode Setup
*	Long-Term Development & Support


### Base Specs:

*	Algo: 		C11
*	Blocktime:	90 sec
*	Maturity: 	90 blocks
*	Diff retargeting: 	every block
*	Total supply: 	Infinite
*	Masternode Rewards: 80% of POS Rewards
*	PoS coins maturation: 2 hours min/unlimited max


#### PoW Rewards:

// miner's coin base reward
int64_t GetProofOfWorkReward(int nHeight, int64_t nFees)
{
    // Base reward.

    int64_t nSubsidy = 0 * COIN;

    if (nHeight == 1) {
        nSubsidy = 375000 * COIN; // premine
    }
    else if (nHeight > 1 && nHeight <= 100) {
        nSubsidy = 2 * COIN; // early adopter 
    }   
    else if (nHeight > 100 && nHeight <= 200) {
        nSubsidy = 10 * COIN; //  early adopter
    }       
    else if (nHeight > 200 && nHeight <= 300) {
        nSubsidy = 20 * COIN; //  early adopter
    }
    else if (nHeight > 300 && nHeight <= 400) {
        nSubsidy = 25 * COIN; //  early adopter
    }   
    else if (nHeight > 400 && nHeight <= 500) {
        nSubsidy = 35 * COIN; //  early adopter
    }   	
    else if (nHeight > 500 && nHeight <= 4800) {
        nSubsidy = 50 * COIN; // initial block reward
    }
    else if (nHeight > 4800 && nHeight <= 50000) {
        nSubsidy = 35 * COIN; // initial block reward
    }
    else if (nHeight > 50000 && nHeight <= 100000) {
        nSubsidy = 25 * COIN; // initial block reward
    }
    else if (nHeight > 100000 && nHeight <= 200000) {
        nSubsidy = 20 * COIN; // initial block reward
    }
    else if (nHeight > 200000 && nHeight <= 300000) {
        nSubsidy = 10 * COIN; // initial block reward
    }
    else if (nHeight > 300000 && nHeight <= 450000) {
        nSubsidy = 5 * COIN; // initial block reward
    }
    else if (nHeight > 450000 && nHeight <= 600000) {
        nSubsidy = 3 * COIN; // initial block reward
    }
    else if (nHeight > 600000 && nHeight <= 900000) {
        nSubsidy = 1 * COIN; // initial block reward
    }
    else if (nHeight > 900000 && nHeight <= 1500000) {
        nSubsidy = 1 / 2 * COIN; // initial block reward
    }
    else if (nHeight > 1500000) {
        nSubsidy = 0 * COIN; // initial block reward
    }
	
    // add fees.
    return nSubsidy + nFees;
}

##### PoS Rewards:

// miner's coin stake reward
int64_t GetProofOfStakeReward(const CBlockIndex* pindexPrev, int64_t nCoinAge, int64_t nFees)
{
    int64_t nSubsidy = 0;

    if (pindexBest->nHeight+1 > 0 && pindexBest->nHeight+1 <= 4801) {
        nSubsidy = (nCoinAge * STATIC_POS_REWARD) / ((365 * 33 + 8) / 33); // 10% per annum.
    }
    else if (pindexBest->nHeight+1 > 4801 && pindexBest->nHeight+1 <= 50000)  {
        nSubsidy = 40 * COIN; 
    }
    else if (pindexBest->nHeight+1 > 50000 && pindexBest->nHeight+1 <= 100000)  {
        nSubsidy = 20 * COIN; 
    }
    else if (pindexBest->nHeight+1 > 100000 && pindexBest->nHeight+1 <= 200000) {
        nSubsidy = 15 * COIN;
    }
    else if (pindexBest->nHeight+1 > 200000 && pindexBest->nHeight+1 <= 300000) {
        nSubsidy = 10 * COIN;
    }
    else if (pindexBest->nHeight+1 > 300000 && pindexBest->nHeight+1 <= 450000) {
        nSubsidy = 5 * COIN;
    }
    else if (pindexBest->nHeight+1 > 450000) {
        nSubsidy = 2 * COIN;
    }
        
    return nSubsidy + nFees;
}

###### License

MoarCoin is released under the terms of the MIT license. See COPYING for more information or see http://opensource.org/licenses/MIT.

