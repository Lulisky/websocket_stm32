ʹ��˵����

1. ��wifiģ��ת����ap��������tcp server��ģʽʱ��
   ��Ҫ��ʼ��һ����־����ʾ��ʱapp��websocket clientδ���ӵ���������
   �磺bool g_is_app_connected = false
   
2. ��app��websocket client���ӵ�������ʱ��
   ��Ҫ�����´���
   if(! g_is_app_connected)
   {
		if(! compute_accept_key())
			return error;
		if(! shake_hand())
			return error;
		g_is_app_connected = true;
		return true;
   }
   ��������������Ϊtrue��ʾapp��websocket client����������ֳɹ���
   �Ѿ��ɹ������Ϸ��������������Ϳ��Ի��ഫ�������ˡ�
   
3. �����������յ�app��websocket client���͹���������ʱ��
   ��Ҫ�����´���
   if(g_is_app_connected)
   {
		if(! analy_data())
			return error;
		//�õ�app������������ݣ����ݴ����g_ws_read_buf��
   }
   
4. ����������Ҫ�������ݸ�app��websocket clientʱ��
   ��Ҫ�����´���
   if(g_is_app_connected)
   {
		if(! response("here fill the data you want to send to app"))
			return error;
		//�������ݸ�app�ɹ�
   }

5. ��app�쳣���߷������쳣�Ͽ�ʱ��
   ��Ҫ�����´���
   g_is_app_connected = false
   
ע��
websocket�ļ����°����ļ��У�
base64.h intLib.h sha1.h ws_share.h websocket.h
ʹ��ʱ������Ҫ����ͷ�ļ�websocket.h���ɣ���Ϊwebsocket.h�Ѿ�����������ͷ�ļ���