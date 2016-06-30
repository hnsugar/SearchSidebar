# SearchSidebar

## һ���ؼ��ʣ�
~~~~
��ϵ���б�  ����bar  ����
~~~~





## ����˵��
    ����bar�кܶ��ˣ��ҿ��˱��˵���һЩ�������������Ǹ��˸ģ�
    1.�����˶����ֺ�������ŵĴ�����#�����ˡ�
    2.��Ե�����ĸ������ͬ���˴���
    3.�������Զ���View��ʽ����ֽ��ʹ�÷��㡣
    
    ���Ĵ��뷽���� mSortBarFilter.setMembers(mMembers, new SearchSideBar.onItemClickListener()
    
## ʾ��
![ image](https://github.com/hnsugar/SearchSidebar/blob/master/SearchSidebar.gif)

 

##  ����

    <com.lujianchao.SearchSideBar.view.SearchSideBar
        android:id="@+id/lv_contact"
        android:layout_width="match_parent"
        android:layout_height="match_parent"></com.lujianchao.SearchSideBar.view.SearchSideBar>
        
##  ����

 
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.mainactivity);
        mSortBarFilter= (SearchSideBar) findViewById(R.id.lv_contact);
        String[] mStrings = getResources().getStringArray(R.array.contacts);
        Uri uri =  Uri.parse(ContentResolver.SCHEME_ANDROID_RESOURCE + "://"
                + getResources().getResourcePackageName(R.mipmap.ic_launcher) + "/"
                + getResources().getResourceTypeName(R.mipmap.ic_launcher) + "/"
                + getResources().getResourceEntryName(R.mipmap.ic_launcher));
        for (int i = 0; i < mStrings.length; i++) {
            Member mMember = new Member();
            mMember.setData(new Member.DataEntity());
            mMember.getData().setMemberID("aaaaaaa" + i);
            mMember.getData().setDispName(mStrings[i]);
            mMember.getData().setLogo(uri.toString());
            mMembers.add(mMember);
        }
        mSortBarFilter.setMembers(mMembers, new SearchSideBar.onItemClickListener() {
            @Override
            public void onItem(int position, SearchSideBar.ContactSortModel mModel) {
                System.out.println("position = [" + position + "], mModel = [" + mModel + "]");
            }
        });
    }