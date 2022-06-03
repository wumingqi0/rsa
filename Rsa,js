'use strict';
var RSA = {};

/**
请谨慎使用无法保证安全性
作者：吴名启
2021年6月2日
 **/
RSA.generate = function(){
    function modular_multiplicative_inverse(a, n){
    	var t  = 0,
            nt = 1,
            r  = n,
            nr = a % n;
        if (n < 0){
        	n = -n;
        }
        if (a < 0){
        	a = n - (-a % n);
        }
    	while (nr !== 0) {
    		var quot= (r/nr) | 0;
    		var tmp = nt;  nt = t - quot*nt;  t = tmp;
    		    tmp = nr;  nr = r - quot*nr;  r = tmp;
    	}
    	if (r > 1) { return -1; }
    	if (t < 0) { t += n; }
    	return t;
    }

    function random_prime(min, max){
        var p = Math.floor(Math.random() * ((max - 1) - min + 1)) + min;
        if(bigInt(p).isPrime()===true){
            return p;
        } else {
            return random_prime(min, max);   
        } 
    }

    var p = random_prime(1, 255), // 8 bit
        q = random_prime(1, 255), // 8 bit
        n = p * q,
        t = (p - 1) * (q - 1), // totient as φ(n) = (p − 1)(q − 1)
        e = random_prime(1, t),
        d = modular_multiplicative_inverse(e, t);
    return {
    	n: n, // public key (part I)
        e: e, // public key (part II)
        d: d  // private key
    };
};

RSA.encrypt = function(m, n, e){
	return bigInt(m).pow(e).mod(n);   
};

RSA.decrypt = function(mEnc, d, n){
	return bigInt(mEnc).pow(d).mod(n);   
};
