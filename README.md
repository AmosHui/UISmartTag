# UISmartTag
##智能标签使用方式:
  1.在布局中引用
  <cn.mwee.smart.tag.UISmartTag
        android:id="@+id/uismarttag"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>
        
  2.实例化标签
  //ShopDetailEvaluateBean.TagList 数据列表
  UISmartTag<ShopDetailEvaluateBean.TagList> uismarttag; //评价标签
  uismarttag = findViewById(R.id.uismarttag);
  uismarttag.setColumnGap((int) DM.dpToPx(8));
        uismarttag.setRowGap((int) DM.dpToPx(8));
        uismarttag.setShowMaxRowCount(2);
        uismarttag.setOnTagViewCallBack(new ITagViewCallBack<ShopDetailEvaluateBean.TagList>() {
            @Override
            public View getView(Context context, ViewGroup viewGroup, final ShopDetailEvaluateBean.TagList tagData, int position) {
                //自定义tagView
                View view = LayoutInflater.from(context).inflate(R.layout.item_tag, viewGroup, false);
                TextView tv_tag = view.findViewById(R.id.tv_tag);
                tv_tag.setText(tagData);
                view.setOnClickListener(new View.OnClickListener() {
                    @Override
                    public void onClick(View view) {
                        Toast.makeText(context, tagData, Toast.LENGTH_SHORT).show();
                    }
                });
                return view;
               
            }
        });
