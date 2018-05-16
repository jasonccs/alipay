/**
 * @var AopAppGateway $gateway
 */
$gateway = Omnipay::create('Alipay_AopPage');
$gateway->setSignType('RSA2'); // RSA/RSA2/MD5
$gateway->setAppId('the_app_id');
$gateway->setPrivateKey('the_app_private_key');
$gateway->setAlipayPublicKey('the_alipay_public_key');
$gateway->setReturnUrl('https://www.example.com/return');
$gateway->setNotifyUrl('https://www.example.com/notify');

/**
 * @var AopTradePagePayResponse $response
 */
$response = $gateway->purchase()->setBizContent([
    'subject'      => 'test',
    'out_trade_no' => date('YmdHis') . mt_rand(1000, 9999),
    'total_amount' => '0.01',
    'product_code' => 'FAST_INSTANT_TRADE_PAY',
])->send();

$url = $response->getRedirectUrl();
For general usage instructions, please see the main Omnipay repository.